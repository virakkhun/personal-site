<script>
	import { base } from '$app/paths';
	import Breadcrumb from '../../components/breadcrumb.svelte';
	import { keyPressEventMap } from '../../shared/constants/key-press-event-map';
	import Title from './components/title.svelte';
	import WorkList from './components/work-list.svelte';

	const breadcrumbs = [
		{ link: `${base}/`, label: 'home' },
		{ link: `${base}/works`, label: 'works' }
	];
</script>

<svelte:head>
	<title>works | virak khun</title>
	<meta name="description" content="virak khun's works experience" />
	<meta property="og:url" content="https://rakdotdev.space/works/" />
	<meta property="og:title" content="works | virak khun" />
	<meta property="og:description" content="virak khun's works experience" />
	<meta name="twitter:url" content="https://rakdotdev.space/works/" />
	<meta name="twitter:title" content="works | virak khun" />
	<meta property="twitter:description" content="virak khun's works experience" />
	<link rel="canonical" href="https://www.rakdotdev.space/works/" />
</svelte:head>

<svelte:document on:keypress={(e) => keyPressEventMap[e.key] && keyPressEventMap[e.key]} />
<Breadcrumb {breadcrumbs} />
<Title />
<WorkList />
