<script context="module" lang="ts">
	export const direction = writable('');
	export const animationStart = writable(false);
</script>

<script lang="ts">
	import FrontSlide from './FrontSlide.svelte';
	import BackSlide from './BackSlide.svelte';
	import Liberated from './Liberated.svelte';
	import Instinctive from './Instinctive.svelte';
	import Visionary from './Visionary.svelte';
	import Free from './Free.svelte';
	import Patron from './Patron.svelte';
	import Reader from './Reader.svelte';
	import Pygmalion from './Pygmalion.svelte';
	import LoverOfTheArts from './LoverOfTheArts.svelte';
	import AvantGarde from './AvantGarde.svelte';
	import Luck from './Luck.svelte';

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
			{`animationStart : ${$animationStart}`} <br />
			{`direction : ${$direction}`}
		</div>
	</div>
	<div class="relative mx-auto h-fit w-fit text-white">
		<svelte:component this={frontSlide.component} position="front" />
		<svelte:component this={backSlide.component} position="rear" />
	</div>
</main>

<style>
</style>
