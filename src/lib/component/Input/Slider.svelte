<script lang="ts">
	export let width: number;
	export let value = 1;
	export let adjusting = false;
	export let primaryColor = 'bg-zinc-600';
	export let secondaryColor = 'bg-zinc-400';
	export let knobColor = 'bg-white';

	let sliderPos = width * value;
	let sliderElement: HTMLElement;

	$: value = 1 * (sliderPos / width);
</script>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<div
	class="relative h-2 w-[--width] rounded-full {primaryColor}"
	style="--width: {width}px;"
	bind:this={sliderElement}
	on:mousedown={(event) => {
		let mouseX = event.clientX;
		let sliderLeft = sliderElement.getBoundingClientRect().left;

		adjusting = true;
		sliderPos = mouseX - sliderLeft;
	}}
	on:dragstart|preventDefault
>
	<div class="h-2 w-[--width] rounded-full {secondaryColor}" style="--width: {sliderPos}px;" />
	<div
		class="absolute -left-2 -top-1 h-4 w-4 translate-x-[--position] rounded-full {knobColor}"
		style="--position: {sliderPos}px;"
	/>
</div>

<svelte:window
	on:mousemove={(event) => {
		if (adjusting === false) {
			return;
		}

		let mouseX = event.clientX;
		let sliderLeft = sliderElement.getBoundingClientRect().left;
		let sliderRight = sliderElement.getBoundingClientRect().right;

		// console.log(
		// 	`mouseX : ${mouseX}\nsliderPos : ${sliderPos}\nsliderLeft : ${sliderLeft}\nsliderRight : ${sliderRight}`
		// ); // debug

		if (mouseX < sliderLeft) {
			sliderPos = 0;
			return;
		}
		if (mouseX > sliderRight) {
			sliderPos = width;
			return;
		}
		sliderPos = mouseX - sliderLeft;
	}}
	on:mouseup={() => {
		adjusting = false;
	}}
/>

<style>
</style>
