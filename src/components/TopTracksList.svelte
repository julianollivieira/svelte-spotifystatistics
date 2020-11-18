<script>
    export let access_token;
    let tracks = [];
    let errors = [];

    axios.get('https://api.spotify.com/v1/me/top/tracks?time_range=long_term&limit=50', {
        headers: {
            'Content-Type': 'applications/json',
            'Authorization': `Bearer ${access_token}`
        }
    }).then(function (response) {
        tracks = response.data.items;
    }).catch(function (error) {
        errors.push(error);
    });
</script>

{#if tracks}
    <div class="list">
        <h1>Top Tracks</h1>
        <table>
            <thead>
                <tr>
                    <th>#</th>
                    <th>Name</th>
                    <th>Image</th>
                </tr>
            </thead>
            <tbody>
                {#each tracks as track, i}
                    <tr>
                        <td class="track-number">{ i + 1}</td>
                        <td>{ track.name }</td>
                        <td><img src="{ track.album.images[0].url }"></td>
                    </tr>
                {/each}
            </tbody>
        </table>
    </div>
{/if}