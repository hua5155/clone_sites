<script lang="ts">
	const variants = ['black', 'white', 'red', 'clear'];
	let selected = variants[0];

	let containerElement: HTMLElement;
	let width = 0;

	let mouseDown = false;
	const onMouseDown = (e: MouseEvent) => {
		mouseDown = true;
	};
	const onMouseUp = (e: MouseEvent) => {
		mouseDown = false;
	};
	const onMouseMove = (e: MouseEvent) => {
		if (mouseDown === false) {
			return;
		}

		let mouseX = e.clientX;
		let boundaryLeft = containerElement.getBoundingClientRect().left;
		let boundaryRight = containerElement.getBoundingClientRect().right;

		if (mouseX < boundaryLeft) {
			width = 0;
			return;
		}
		if (mouseX > boundaryRight) {
			width = 800;
			return;
		}
		width = mouseX - boundaryLeft;
	};
</script>

<main class="h-fit w-screen max-w-full bg-black">
	<div class="flex flex-row space-x-5">
		<div class="relative h-[800px] w-[800px]" bind:this={containerElement}>
			<div class="relative h-fit w-[--width] overflow-hidden" style:--width="{width}px">
				<img
					class="w-[800px] max-w-[800px]"
					src={`pulsar/X2_mini_${selected}_bot.webp`}
					alt=""
					on:dragstart|preventDefault
				/>
			</div>
			<div
				class="absolute right-0 top-0 h-[800px] w-[--width] overflow-hidden"
				style:--width="{800 - width}px"
			>
				<img
					class="absolute right-0 top-0 w-[800px] max-w-[800px]"
					src={`pulsar/X2_mini_${selected}_top.webp`}
					alt=""
					on:dragstart|preventDefault
				/>
			</div>
			<div
				class="absolute left-[--position] top-0 h-full w-2 [cursor:ew-resize] [user-select:none]"
				style:--position="{width - 4}px"
				on:mousedown={(e) => {
					onMouseDown(e);
				}}
				on:dragstart|preventDefault
			>
				<div class="mx-auto h-full w-0.5 bg-blue-600 opacity-70" />
			</div>
		</div>

		<div class="mt-10">
			<select class="block" bind:value={selected}>
				{#each variants as variant}
					<option value={variant}>{variant}</option>
				{/each}
			</select>
			<input class="" type="range" min="0" max="800" bind:value={width} />
			<p class="text-white">{`variant : ${selected}`}</p>
			<p class="text-white">{`width : ${width}`}</p>
		</div>
	</div>
</main>

<svelte:window
	on:mouseup={(e) => {
		onMouseUp(e);
	}}
	on:mousemove={(e) => {
		onMouseMove(e);
	}}
/>

<style>
	/*  */
</style>
