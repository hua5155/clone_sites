<script lang="ts">
	import { z } from 'zod';
	const isArray = z.array(z.string());

	export let url: string | string[];
	let nestedFlag = false;
	let urlArray = [''];
	let zResult = isArray.safeParse(url);
	if (zResult.success === true) {
		nestedFlag = true;
		urlArray = zResult.data;
	}
</script>

{#if nestedFlag}
	<ul class="my-2 hidden text-[11px] md:block">
		{#each urlArray as url}
			<li>{`${url} -`}</li>
		{/each}
	</ul>
	<ul class="my-6 text-[14px] leading-[21px] md:hidden">
		{#each urlArray as url}
			<li>{`- ${url}`}</li>
		{/each}
	</ul>
{:else}
	<li>{url}</li>
{/if}

<style>
</style>
