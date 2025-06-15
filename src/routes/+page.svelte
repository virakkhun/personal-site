<script lang="ts">
	import ThemeSwitcher from '../components/theme-switcher.svelte';
	import CopyRight from './components/copy-right.svelte';
	import EmailMe from './components/email-me.svelte';
	import Hero from './components/hero.svelte';
	import Nav from './components/nav.svelte';
	import Social from './components/social.svelte';
</script>

<svelte:head>
	<title>virak khun</title>
	<meta
		name="description"
		content="virak is a software engineer based in phnom penh, graduated from rupp majored in computer science"
	/>
	<meta name="keywords" content="virakkhun, khunvirak, khun virak, virak dev" />
	<meta property="og:title" content="virak khun" />
	<meta
		property="og:description"
		content="virak a software engineer based in phnom penh, graduated from rupp majored in computer science"
	/>
	<meta property="og:url" content="https://www.rakdotdev.space/" />
	<meta property="og:site_name" content="virak khun" />
	<meta property="og:locale" content="en-US" />
	<meta
		property="og:image"
		content="https://media.licdn.com/dms/image/v2/D5603AQE6EDPn_HqMdw/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1695958815370?e=2147483647&v=beta&t=9brfW4HANqoNceE_xNf4ebRtnLIcHPvZGrrDJdIuW74"
	/>

	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:url" content="https://www.rakdotdev.space/" />
	<meta name="twitter:domain" content="rakdotdev.space" />
	<meta name="twitter:title" content="virak khun" />
	<meta
		property="twitter:description"
		content="virak a software engineer based in phnom penh, graduated from rupp majored in computer science"
	/>
	<meta
		property="twitter:image"
		content="https://media.licdn.com/dms/image/v2/D5603AQE6EDPn_HqMdw/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1695958815370?e=2147483647&v=beta&t=9brfW4HANqoNceE_xNf4ebRtnLIcHPvZGrrDJdIuW74"
	/>
	<link rel="canonical" href="https://www.rakdotdev.space/" />

	<script type="application/ld+json">
		{
			"@context": "https://schema.org",
			"@type": "Person",
			"images": "https://media.licdn.com/dms/image/v2/D5603AQE6EDPn_HqMdw/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1695958815370?e=2147483647&v=beta&t=9brfW4HANqoNceE_xNf4ebRtnLIcHPvZGrrDJdIuW74",
			"name": "virak khun",
			"email": "mailto:dev.virakkhun@gmail.com",
			"url": "https://www.rakdotdev.space/",
			"description": "virak a software engineer based in phnom penh, graduated from rupp majored in computer science",
			"jobTitle": "Software Engineer"
		}
	</script>
</svelte:head>

<div class="w-full h-svh md:py-24 pt-24 pb-4 flex flex-col justify-between items-start">
	<div>
		<ThemeSwitcher />
		<Hero />
		<Social />
		<Nav />
	</div>

	<div class="flex flex-col gap-2">
		<EmailMe />
		<CopyRight />
	</div>
</div>
