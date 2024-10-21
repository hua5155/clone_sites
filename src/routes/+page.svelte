<script lang="ts">
	let urls = [
		{
			href: '/about-chanel',
			text: 'About CHANEL'
		},
		{
			href: '/social-coffee-house',
			text: 'Social Coffee House'
		},
		{
			href: '/botanist',
			text: 'BOTANIST (RWD)'
		},
		{
			href: '/pulsar-x2-mini',
			text: 'Pulsar X2 mini'
		}
	];
</script>

<main class="h-fit min-h-lvh w-dvw bg-black p-10 font-semibold text-gray-200 xl:p-20">
	<h1 class="text-3xl text-gray-500">Disclaimers</h1>
	<ol class="list-outside list-decimal space-y-5 pl-8 pt-5 text-sm xl:text-2xl xl:[&>li]:w-[70ch]">
		<li>
			I didn't work for any of these websites, I'm just trying to practice Svelte &Tailwind by
			copying these websites.
		</li>
		<li>
			I do not own the copyright to the assests I used, If I violated your IP please notify me at
			s17115155@stu.edu.tw, I will remove the page.
		</li>
	</ol>

	<div class="w-full pt-20"></div>
	<h1 class="text-3xl text-gray-500">Websites</h1>
	<ul class="space-y-2 pt-5 text-xl xl:text-2xl">
		{#each urls as url}
			<li>
				<a class="" href={url.href}>{url.text}</a>
			</li>
		{/each}
	</ul>
</main>

<style></style>
