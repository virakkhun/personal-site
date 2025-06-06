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
</script>

<svelte:head>
	<title>{data.title.replace(/-/g, ' ')}</title>
	<meta name="description" content={data.content} />

	<meta name="description" content={data.content} />
	<meta property="og:url" content="https://rakdotdev.space/blogs/{data.title.replace(/-/g, ' ')}" />
	<meta property="og:title" content={data.title} />
	<meta property="og:description" content={data.content} />
	<meta
		name="twitter:url"
		content="https://rakdotdev.space/blogs/{data.title.replace(/-/g, ' ')}"
	/>
	<meta name="twitter:title" content={data.title.replace(/-/g, ' ')} />
	<meta property="twitter:description" content={data.content} />
</svelte:head>

{#if data?.content}
	<Breadcrumb
		breadcrumbs={[...breadcrumbs, { label: data?.title, link: `${base}/blogs/${data?.title}` }]}
	/>
	<BlogDetailWrapper>
		<Markdown content={data?.content} />
	</BlogDetailWrapper>
{/if}
