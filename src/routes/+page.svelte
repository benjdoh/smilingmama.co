<script lang="ts">
	import { onMount } from 'svelte';

	type Props = {
		player: any;
	};

	const YT_PLAYER_ID = 'youtube-video';
	let { player }: Props = $props();

	onMount(() => {
		function load() {
			// @ts-expect-error - YT is a global variable
			player = new YT.Player(YT_PLAYER_ID, {
				height: '100%',
				width: '100%',
				videoId: '2709u_t793w',
				playerVars: { autoplay: 1, mute: 1, controls: 0, loop: 1, rel: 0, playlist: '2709u_t793w' },
				events: {
					onReady: updatePlayerSize
				}
			});
		}

		function updatePlayerSize() {
			if (window.innerWidth >= 1280) player.setSize(1280, 720);
			else player.setSize(window.innerWidth, window.innerWidth * 0.5625);
		}

		// @ts-expect-error - YT is a global variable
		if (window.YT) {
			load();
		} else {
			// @ts-expect-error - onYouTubeIframeAPIReady is a global variable
			window.onYouTubeIframeAPIReady = load;
		}

		window.onresize = updatePlayerSize;
	});
</script>

<svelte:head>
	<script src="https://www.youtube.com/iframe_api"></script>
</svelte:head>

<div class="relative mx-auto w-screen max-w-7xl overflow-hidden grid place-items-center">
	<div id={YT_PLAYER_ID}></div>
</div>

<div class="p-16">
	<div class="mx-auto max-w-7xl text-center text-4xl">
		Smiling Mama, Bowling Green's newest takeout, serves up an explosion of authentic Thai and
		Burmese flavors. Dive into vibrant curries, savory noodle dishes, and unique regional
		specialties, all crafted with ingredients and bursting with character.
	</div>
</div>
