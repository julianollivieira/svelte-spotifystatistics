<script>
	import SpotifyLoginButton from './components/SpotifyLoginButton.svelte';
	import TopArtistsList from './components/TopArtistsList.svelte';
	import TopTracksList from './components/TopTracksList.svelte';

	let url = new URL(window.location.href);
	let error = url.searchParams.get('error');
	let access_token = window.location.hash.substr(1).replace("access_token=", "");
</script>

<div class="container">
	<div class="header">
		<h1>Spotify Statistics</h1>
		<SpotifyLoginButton { access_token } />
	</div>
	<hr>
	<div class="lists">
		{#if access_token}
			<TopArtistsList { access_token } />
			<TopTracksList { access_token } />
		{/if}
	</div>
</div>