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
			text: 'BOTANIST'
		},
		{
			href: '/pulsar_x2_mini',
			text: 'Pulsar X2 mini'
		}
	];
</script>

<main class="h-screen w-screen bg-black p-20 text-3xl font-semibold text-white">
	<ul class="space-y-2">
		{#each urls as url}
			<li>
				<a class="" href={url.href}>{url.text}</a>
			</li>
		{/each}
	</ul>
</main>

<style></style>
