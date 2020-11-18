<script>
    export let access_token;
    let artists = [];
    let errors = [];

    axios.get('https://api.spotify.com/v1/me/top/artists', {
        headers: {
            'Content-Type': 'applications/json',
            'Authorization': `Bearer ${access_token}`
        }
    }).then(function (response) {
        artists = response.data.items;
    }).catch(function (error) {
        errors.push(error);
    });
</script>

{#if artists}
    <div class="list">
        <h1>Top Artists</h1>
        <table>
            <thead>
                <tr>
                    <th>#</th>
                    <th>Name</th>
                    <th>Image</th>
                </tr>
            </thead>
            <tbody>
                {#each artists as artist, i}
                    <tr>
                        <td>{ i + 1}</td>
                        <td>{ artist.name }</td>
                        <td><img src="{ artist.images[0].url }"></td>
                    </tr>
                {/each}
            </tbody>
        </table>
    </div>
{/if}