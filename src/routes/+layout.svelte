<script lang="ts">
	import '@unocss/reset/tailwind.css';
	import 'virtual:uno.css';
	import Logo from '$lib/components/smiling mama logo.svelte';

	const NAV_LINK_CLASS =
		'hover:underline underline-2 underline-offset-4 h-12 grid place-items-center';
</script>

<div class="sticky top-0 w-screen p-4 border-b-5 border-[#f70203] z-200 bg-white">
	<div class="max-w-7xl mx-auto h-20 flex items-center gap-4 justify-between font-semibold">
		<a href="/">
			<Logo class="h-20" />
		</a>

		<div class="flex gap-8 items-center h-12 text-lg">
			<a href="/menu" class={NAV_LINK_CLASS}>Menu</a>
			<a href="/about" class={NAV_LINK_CLASS}>About</a>
			<a href="/contact" class={NAV_LINK_CLASS}>Contact</a>

			<a
				href="/order"
				class="border-2 border-[#f70203] text-[#f70203] rounded py-2 px-4 hover:text-white hover:bg-[#f70203] transition-colors duration-300 ease-in-out"
			>
				Order Pickup
			</a>
		</div>
	</div>
</div>

<slot />

<svelte:head>
	<title>Smiling Mama</title>
	<link rel="icon" href="/favicon.png" />
</svelte:head>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');

	:global(body) {
		font-family: 'Inter', sans-serif;
	}
</style>
