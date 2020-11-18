<script>
    function uuidv4() {
		return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
			var r = Math.random() * 16 | 0, v = c == 'x' ? r : (r & 0x3 | 0x8);
			return v.toString(16);
		});
    }
    
    function spotifyLoginClick() {
		const client_id = '7f1c1bd62e4f4bfe9b604b7dd8dcc672';
		// const redirect_uri = 'https:%2F%2Fsvelte-spotifystatistics.netlify.app';
        const redirect_uri = 'http:%2F%2Flocalhost:5000';
        const state = uuidv4();
		window.location.href = `https://accounts.spotify.com/authorize?client_id=${client_id}&response_type=token&redirect_uri=${redirect_uri}&state=${state}&scope=user-top-read`;
	}
</script>

<button on:click={spotifyLoginClick}>
    <img src="spotify_Icon_RGB_White.png" alt="Spotify Icon">
    <p>Login with Spotify</p>
</button>