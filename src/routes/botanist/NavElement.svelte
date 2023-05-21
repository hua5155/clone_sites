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
	<ul class="my-2 text-[11px] leading-[23px]">
		{#each urlArray as url}
			<li>{url}</li>
		{/each}
	</ul>
{:else}
	<li>{url}</li>
{/if}

<style>
</style>
