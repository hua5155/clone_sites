<script lang="ts">
	import Slide from '$lib/component/Chanel/About_Chanel/Slide.svelte';
	import {
		direction,
		animationStart,
		frontIndex,
		backIndex
	} from '$lib/component/Chanel/About_Chanel/Slide.svelte';

	const slides = [
		'Liberated',
		'Instinctive',
		'Visionary',
		'Free',
		'Patron',
		'Reader',
		'Pygmalion',
		'LoverOfTheArts',
		'AvantGarde',
		'Luck'
	];
</script>

<div class="z-50 mx-auto flex w-fit flex-row space-x-5 py-10 text-black">
	<button
		class="h-10 w-fit rounded-lg bg-cyan-500 px-5"
		on:click={() => {
			$animationStart = !$animationStart;
		}}
	>
		Toggle animationStart
	</button>

	<button
		class="h-10 w-fit rounded-lg bg-cyan-500 px-5"
		on:click={() => {
			$direction = 'left';
		}}
	>
		Left
	</button>

	<button
		class="h-10 w-fit rounded-lg bg-cyan-500 px-5"
		on:click={() => {
			$direction = 'right';
		}}
	>
		Right
	</button>

	<div class="flex flex-row space-x-5">
		<select class="h-10 w-fit rounded-lg px-5" bind:value={$frontIndex}>
			{#each slides as slide, index}
				<option value={index}>{slide}</option>
			{/each}
		</select>
	</div>

	<div class="flex flex-row space-x-5">
		<select class="h-10 w-fit rounded-lg px-5" bind:value={$backIndex}>
			{#each slides as slide, index}
				<option value={index}>{slide}</option>
			{/each}
		</select>
	</div>

	<div class="w-fit rounded-lg bg-white px-5 py-5">
		{`animationStart : ${$animationStart}`} <br />
		{`direction : ${$direction}`}
	</div>
</div>
<Slide />

<style>
</style>
