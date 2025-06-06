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
	<meta name="referrer" content="no-referrer" />
	<meta name="theme-color" content="#1A1A1A" />
	<meta name="color-scheme" content="dark" />
	<meta name="viewport" content="width=device-width, initial-scale=1" />
	<meta name="creator" content="virakkhun" />
</svelte:head>

<svelte:document on:keypress={onKeyPress} />

<main class="container mx-auto md:px-24 px-4 relative">
	<slot />
</main>

<KeymapStore keymaps={localEvent} />
<Keymaps bind:this={keyMapsRef} />
