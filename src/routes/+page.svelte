<script lang="ts">
	let urls = [
		{
			href: '/about_chanel',
			text: 'About CHANEL'
		},
		{
			href: '/social_coffee_house',
			text: 'Social Coffee House'
		},
		{
			href: '/botanist',
			text: 'BOTANIST (RWD)'
		},
		{
			href: '/pulsar_x2_mini',
			text: 'Pulsar X2 mini'
		}
	];
</script>

<main class="h-screen w-screen bg-black p-20 text-3xl font-semibold text-gray-200">
	<h1 class="w-[60ch]">
		<span class="text-gray-500">Disclaimers</span>
		<ol class="list-outside list-decimal space-y-5 pl-8 pt-5">
			<li>
				I didn't work for any of these websites, I'm just trying to practice Svelte &Tailwind by
				copying these websites.
			</li>
			<li>
				I do not own the copyright to the assests I used, If I violated your IP please notify me at
				s17115155@stu.edu.tw, I will remove the page.
			</li>
		</ol>
	</h1>

	<div class="pt-20">
		<span class="text-gray-500">Websites</span>
		<ul class="space-y-2 pt-5">
			{#each urls as url}
				<li>
					<a class="" href={url.href}>{url.text}</a>
				</li>
			{/each}
		</ul>
	</div>
</main>

<style></style>
