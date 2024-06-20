<script lang="ts">
	const VARIANTS = ['black', 'white', 'red', 'clear'] as const;
	const IMG_WIDTH = 600 as const;

	let selected = VARIANTS[0] as string;
	let quantity = 1;

	let containerElement: HTMLElement;
	let width = IMG_WIDTH / 2;

	let mouseDown = false;
</script>

<main
	class="flex h-fit min-h-screen w-screen max-w-full flex-col items-center bg-black text-[#e8e8e8]"
>
	<div class="flex flex-row space-x-5 px-10 pt-10">
		<div
			class="relative aspect-square w-[--width]"
			style:--width="{IMG_WIDTH}px"
			bind:this={containerElement}
		>
			<div class="h-full w-[--width] overflow-hidden" style:--width="{width}px">
				<img
					class="max-w-[--width]"
					style:--width="{IMG_WIDTH}px"
					src={`pulsar/X2_mini_${selected}_bot.webp`}
					alt=""
					on:dragstart|preventDefault
				/>
			</div>
			<div
				class="absolute right-0 top-0 h-full w-[--width] overflow-hidden"
				style:--width="{IMG_WIDTH - width}px"
			>
				<img
					class="absolute right-0 top-0 max-w-[--width]"
					style:--width="{IMG_WIDTH}px"
					src={`pulsar/X2_mini_${selected}_top.webp`}
					alt=""
					on:dragstart|preventDefault
				/>
			</div>
			<div
				class="absolute left-[--position] top-0 flex h-full w-2 justify-center [cursor:ew-resize] [user-select:none]"
				style:--position="{width - 3}px"
				role="none"
				on:mousedown={(event) => {
					mouseDown = true;
				}}
				on:dragstart|preventDefault
			>
				<div class="h-full w-0.5 bg-[#0080ff] opacity-70" />
			</div>
		</div>

		<div class="w-[600px]">
			<h1 class="w-fit pt-5 text-5xl font-bold [&::first-letter]:uppercase">
				{`${selected} X2 v2 Mini`}
			</h1>
			<p class="w-fit pt-2 text-xl font-bold">$99.95</p>
			<div class="flex w-fit flex-row space-x-2 pt-10">
				{#each VARIANTS as variant}
					<button
						on:click={() => {
							selected = variant;
						}}
					>
						<img
							class="w-[100px] border border-gray-500"
							src={`pulsar/X2_mini_${variant}_top.webp`}
							alt=""
						/>
					</button>
				{/each}
			</div>

			<div class="pt-10"></div>

			<p class="w-fit">Quantity</p>
			<div class="flex h-fit w-fit flex-row rounded-lg border border-gray-500">
				<button
					class="px-2 text-sm font-light"
					on:click={() => {
						if (quantity === 1) return;
						quantity -= 1;
					}}
				>
					-
				</button>
				<input
					class="h-9 w-8 bg-transparent text-center [appearance:none] focus:outline-none"
					type="number"
					bind:value={quantity}
				/>
				<button
					class="px-2 text-sm font-light"
					on:click={() => {
						quantity += 1;
					}}
				>
					+
				</button>
			</div>

			<div class="pt-10"></div>

			<button class="w-full rounded-lg bg-[#0080ff] py-3 text-sm font-bold">ADD TO CART</button>
		</div>
	</div>
</main>

<svelte:window
	on:mouseup={(event) => {
		mouseDown = false;
	}}
	on:mousemove={(event) => {
		if (mouseDown === false) {
			return;
		}

		let mouseX = event.clientX;
		let boundaryLeft = containerElement.getBoundingClientRect().left;
		let boundaryRight = containerElement.getBoundingClientRect().right;

		if (mouseX < boundaryLeft) {
			width = 0;
			return;
		}
		if (mouseX > boundaryRight) {
			width = IMG_WIDTH;
			return;
		}
		width = mouseX - boundaryLeft;
	}}
/>

<style>
	/* Hide number input arrows */
	input::-webkit-outer-spin-button,
	input::-webkit-inner-spin-button {
		-webkit-appearance: none;
		margin: 0;
	}
	input[type='number'] {
		-moz-appearance: textfield;
	}
</style>
