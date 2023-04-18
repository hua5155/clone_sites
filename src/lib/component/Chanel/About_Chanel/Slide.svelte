<script context="module" lang="ts">
	export const direction = writable('');
	export const animationStart = writable(false);
	// export const animationEnd = writable(false);
	export const frontIndex = writable(0);
	export const backIndex = writable(0);
</script>

<script lang="ts">
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
		Liberated,
		Instinctive,
		Visionary,
		Free,
		Patron,
		Reader,
		Pygmalion,
		LoverOfTheArts,
		AvantGarde,
		Luck
	];
	let frontSlide = slides[$frontIndex];
	let backSlide = slides[$backIndex];
	$: frontSlide = slides[$frontIndex];
	$: backSlide = slides[$backIndex];
</script>

<div class="relative h-fit w-full">
	<svelte:component this={frontSlide} position="front" />
	<svelte:component this={backSlide} position="rear" />
</div>

<style>
</style>
