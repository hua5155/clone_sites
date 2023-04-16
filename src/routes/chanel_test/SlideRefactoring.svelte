<script context="module" lang="ts">
	const direction = writable('');
	const animationStart = writable(false);
</script>

<script lang="ts">
	import FrontSlide from '$lib/component/Chanel/FrontSlide.svelte';
	import BackSlide from '$lib/component/Chanel/BackSlide.svelte';
	import Liberated from '$lib/component/Chanel/Liberated.svelte';
	import Instinctive from '$lib/component/Chanel/Instinctive.svelte';
	import Visionary from '$lib/component/Chanel/Visionary.svelte';
	import Free from '$lib/component/Chanel/Free.svelte';
	import Patron from '$lib/component/Chanel/Patron.svelte';
	import Reader from '$lib/component/Chanel/Reader.svelte';
	import Pygmalion from '$lib/component/Chanel/Pygmalion.svelte';
	import LoverOfTheArts from '$lib/component/Chanel/LoverOfTheArts.svelte';
	import AvantGarde from '$lib/component/Chanel/AvantGarde.svelte';
	import Luck from '$lib/component/Chanel/Luck.svelte';

	import { writable } from 'svelte/store';

	const slides = [
		{
			image: '/Chanel/Slide/liberated.webp',
			component: Liberated
		},
		{
			image: '/Chanel/Slide/instinctive.webp',
			component: Instinctive
		},
		{
			image: '/Chanel/Slide/visionary.webp',
			component: Visionary
		},
		{
			image: '/Chanel/Slide/free.webp',
			component: Free
		},
		{
			image: '/Chanel/Slide/patron.webp',
			component: Patron
		},
		{
			image: '/Chanel/Slide/reader.webp',
			component: Reader
		},
		{
			image: '/Chanel/Slide/pygmalion.webp',
			component: Pygmalion
		},
		{
			image: '/Chanel/Slide/lover_of_the_arts.webp',
			component: LoverOfTheArts
		},
		{
			image: '/Chanel/Slide/avant_garde.webp',
			component: AvantGarde
		},
		{
			image: '/Chanel/Slide/luck.webp',
			component: Luck
		}
	];
	let frontSlide = slides[0];
	let backSlide = slides[1];

	// let direction = '';
	// let animationStart = false;
</script>

<main class="h-fit w-screen bg-black">
	<!-- Div width control -->
	<div class="z-50 mx-auto w-fit py-10">
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
			<span class="text-white">frontSlide</span>
			<select class="h-10 w-fit rounded-lg px-5" bind:value={frontSlide}>
				{#each slides as slide}
					<option value={slide}>{slide.image}</option>
				{/each}
			</select>
		</div>

		<div class="flex flex-row space-x-5">
			<span class="text-white">backSlide</span>
			<select class="h-10 w-fit rounded-lg px-5" bind:value={backSlide}>
				{#each slides as slide}
					<option value={slide}>{slide.image}</option>
				{/each}
			</select>
		</div>

		<div class="w-fit rounded-lg bg-white px-5 py-5">
			{`animationStart : ${animationStart}`} <br />
			{`direction : ${$direction}`}
		</div>
	</div>
	<div class="mx-auto h-fit w-fit text-white">
		<FrontSlide imgSrc={frontSlide.image}>
			<!-- <h3 let:headingStyle class={headingStyle} slot="heading">heading</h3> -->
			<!-- <blockquote let:quoteStyle class={quoteStyle} slot="quote">quotes</blockquote> -->
			<svelte:component this={frontSlide.component} />
			<!-- <Liberated bind:animationStart bind:direction /> -->
		</FrontSlide>

		<BackSlide imgSrc={backSlide.image}>
			<svelte:component this={backSlide.component} />
			<!-- <Instinctive bind:animationStart bind:direction /> -->
		</BackSlide>
	</div>
</main>

<style>
</style>
