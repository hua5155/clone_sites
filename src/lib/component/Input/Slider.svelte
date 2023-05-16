<script lang="ts">
	export let sliderLength = 320;
	export let sliderPos = 0;
	let sliderElement: HTMLElement;

	export let adjusting = false;

	export let primaryColor: string;
	export let secondaryColor: string;
	export let knobColor: string;

	const onMouseDown = (e: MouseEvent) => {
		adjusting = true;
	};
	const onMouseUp = (e: MouseEvent) => {
		adjusting = false;
	};
	const onMouseMove = (e: MouseEvent) => {
		if (adjusting === false) {
			return;
		}

		let mouseX = e.clientX;
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
			sliderPos = sliderLength;
			return;
		}
		sliderPos = mouseX - sliderLeft;
	};
	const onMouseClick = (e: MouseEvent) => {
		let mouseX = e.clientX;
		let sliderLeft = sliderElement.getBoundingClientRect().left;

		sliderPos = mouseX - sliderLeft;
	};
</script>

<div
	class="relative z-0 h-2 rounded-full {primaryColor}"
	style="width: {sliderLength}px;"
	bind:this={sliderElement}
	on:mousedown={(e) => {
		onMouseClick(e);
		onMouseDown(e);
	}}
	on:dragstart|preventDefault
>
	<div
		class="absolute left-0 top-0 z-10 h-2 rounded-full {secondaryColor}"
		style="width: {sliderPos}px;"
		on:dragstart|preventDefault
	/>
	<div
		class="move-slider absolute -left-2 -top-1 z-20 h-4 w-4 rounded-full {knobColor}"
		style="--position: {sliderPos}px;"
		on:mousedown={(e) => {
			onMouseDown(e);
		}}
	/>
</div>
<!-- <input class="h-10 px-5" type="number" bind:value={sliderPos} /> -->

<svelte:window
	on:mousemove={(e) => {
		onMouseMove(e);
	}}
	on:mouseup={(e) => {
		onMouseUp(e);
	}}
/>

<style>
	.move-slider {
		transform: translateX(var(--position));
	}
</style>
