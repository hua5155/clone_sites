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
	<!-- Desktop -->
	<div class="hidden w-full pt-2 md:block"></div>
	<ul class="hidden flex-col items-end text-[11px] md:flex">
		{#each urlArray as url}
			<li class="w-fit cursor-pointer">{`${url} -`}</li>
		{/each}
	</ul>
	<div class="hidden w-full pb-2 md:block"></div>

	<!-- Mobile -->
	<div class="pt-6 md:hidden"></div>
	<ul class="flex flex-col items-start text-[14px] leading-[21px] md:hidden">
		{#each urlArray as url}
			<li class="w-fit cursor-pointer">{`- ${url}`}</li>
		{/each}
	</ul>
	<div class="pb-6 md:hidden"></div>
{:else}
	<li class="w-fit cursor-pointer">{url}</li>
{/if}

<style>
</style>
