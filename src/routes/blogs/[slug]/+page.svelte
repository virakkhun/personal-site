<script lang="ts">
	import { base } from '$app/paths';
	import Breadcrumb from '../../../components/breadcrumb.svelte';
	import Markdown from '../../../components/markdown.svelte';
	import type { PageServerData } from '../[slug]/$types';
	import BlogDetailWrapper from './components/blog-detail-wrapper.component.svelte';

	export let data: PageServerData;
	const breadcrumbs = [
		{ link: `${base}/`, label: 'home' },
		{ link: `${base}/blogs`, label: 'blogs' }
	];
	const title = data.title.replace(/-/g, ' ');
</script>

<svelte:head>
	<title>{title}</title>
	<meta name="description" content={data.content} />
	<meta property="og:url" content="https://rakdotdev.space/blogs/{title}/" />
	<meta property="og:title" content={title} />
	<meta property="og:description" content={data.content} />
	<meta name="twitter:url" content="https://rakdotdev.space/blogs/{title}/" />
	<meta name="twitter:title" content={title} />
	<meta property="twitter:description" content={data.content} />
	<link rel="canonical" href="https://www.rakdotdev.space/blogs/{title}/" />
</svelte:head>

{#if data?.content}
	<Breadcrumb
		breadcrumbs={[...breadcrumbs, { label: data?.title, link: `${base}/blogs/${data?.title}` }]}
	/>
	<BlogDetailWrapper>
		<Markdown content={data?.content} />
	</BlogDetailWrapper>
{/if}
