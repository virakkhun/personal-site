<script lang="ts">
	import { afterNavigate, onNavigate } from '$app/navigation';
	import '../app.css';
	import KeymapStore from '../components/keymap-store.svelte';
	import Keymaps from '../components/keymaps.svelte';
	import { keyPressEventMap, type KeyPressEvent } from '../shared/constants/key-press-event-map';

	const localEvent: KeyPressEvent = {
		...keyPressEventMap,
		x: { func: close, desc: 'close shortcuts menu', type: 'event' },
		K: { func: toggle, desc: 'toggle shortcuts menu', type: 'event' }
	};

	let keyMapsRef: Keymaps;

	function toggle() {
		keyMapsRef.toogle();
	}

	function close() {
		keyMapsRef.close();
	}

	function onKeyPress(e: KeyboardEvent) {
		localEvent[e.key] && localEvent[e.key].func();
	}

	onNavigate((navigation) => {
		if (!document.startViewTransition) return;

		return new Promise((resolve) => {
			document.startViewTransition(async () => {
				resolve();
				await navigation.complete;
			});
		});
	});

	afterNavigate(() => {
		close();
	});
</script>

<svelte:head>
	<title>Virak Khun</title>
	<meta
		name="description"
		content="a Software Engineer based in Phnom Penh, graduated from RUPP majored in Computer Science"
	/>
	<meta name="keywords" content="virakkhun,khunvirak,khun virak,virak dev" />
	<meta name="referrer" content="no-referrer" />
	<meta name="theme-color" content="#1A1A1A" />
	<meta name="color-scheme" content="dark" />
	<meta name="viewport" content="width=device-width, initial-scale=1" />
	<meta name="creator" content="virakkhun" />
	<meta property="og:title" content="Virak Khun" />
	<meta
		property="og:description"
		content="a Software Engineer based in Phnom Penh, graduated from RUPP majored in Computer Science"
	/>
	<meta property="og:url" content="https://rakdotdev.space" />
	<meta property="og:site_name" content="VIRAK KHUN" />
	<meta property="og:locale" content="en-US" />
	<meta
		property="og:image"
		content="https://media.licdn.com/dms/image/v2/D5603AQE6EDPn_HqMdw/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1695958815370?e=2147483647&v=beta&t=9brfW4HANqoNceE_xNf4ebRtnLIcHPvZGrrDJdIuW74"
	/>

	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:url" content="https://rakdotdev.space" />
	<meta name="twitter:domain" content="rakdotdev.space" />
	<meta name="twitter:title" content="Virak Khun" />
	<meta
		property="twitter:description"
		content="a Software Engineer based in Phnom Penh, graduated from RUPP majored in Computer Science"
	/>
	<meta
		property="twitter:image"
		content="https://media.licdn.com/dms/image/v2/D5603AQE6EDPn_HqMdw/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1695958815370?e=2147483647&v=beta&t=9brfW4HANqoNceE_xNf4ebRtnLIcHPvZGrrDJdIuW74"
	/>

	<script type="application/ld+json">
		{
			"@context": "https://schema.org",
			"@type": "Person",
			"images": "https://media.licdn.com/dms/image/v2/D5603AQE6EDPn_HqMdw/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1695958815370?e=2147483647&v=beta&t=9brfW4HANqoNceE_xNf4ebRtnLIcHPvZGrrDJdIuW74",
			"name": "Virak Khun",
			"email": "mailto:dev.virakkhun@gmail.com",
			"url": "https://rakdotdev.space",
			"description": "a Software Engineer based in Phnom Penh, graduated from RUPP majored in Computer Science",
			"jobTitle": "Software Engineer"
		}
	</script>
</svelte:head>

<svelte:document on:keypress={onKeyPress} />

<main class="container mx-auto md:px-24 px-4 relative">
	<slot />
</main>

<KeymapStore keymaps={localEvent} />
<Keymaps bind:this={keyMapsRef} />
