<script lang="ts">
	import Slider from '$lib/component/Input/Slider.svelte';

	export let slide: string;
	export let selected = false;
	let video = `Chanel/Video/${slide}/main.mp4`;
	let preview = `Chanel/Video/${slide}/preview.mp4`;

	let duration: number;
	let currentTime = 0;
	let paused = true;
	let volume = 1;
	let muted = false;
	let playState = false;

	let previewFlag = true;
	let preveiwCurrentTime = 0;
	let previewAutoPlay = false;
	let previewPaused = true;
	$: if (selected === false) {
		preveiwCurrentTime = 0;
		previewPaused = true;
		previewFlag = true;
	} else {
		setTimeout(() => {
			previewAutoPlay = true;
			previewPaused = false;
		}, 1000);
	}

	let timelinePos = 0;
	$: timelinePos = currentTime / duration;

	const VOLUME_SLIDER_WIDTH = 100 as const;
</script>

<div class="group relative h-fit w-fit overflow-hidden">
	<video
		class="h-[720px] max-w-fit"
		src={video}
		bind:currentTime
		bind:duration
		bind:paused
		bind:volume
		bind:muted
	>
		<track kind="captions" />
	</video>

	<div class="absolute bottom-5 left-1/2 -translate-x-1/2">
		<div
			class="flex translate-y-full flex-row items-center justify-center space-x-5 rounded-lg bg-zinc-800 bg-opacity-80 px-7 py-5 opacity-0 transition-all duration-500 hover:bg-opacity-100 group-hover:translate-y-0 group-hover:opacity-100"
		>
			<button
				class="h-10 rounded-lg bg-blue-500 px-5 pb-1"
				on:click={() => {
					paused = !paused;
					playState = !paused;
				}}
			>
				{paused ? 'paused' : 'playing'}
			</button>
			<input
				class="w-[320px] bg-transparent"
				type="range"
				name="timeline"
				id="timeline"
				bind:value={timelinePos}
				min="0"
				max="1"
				step="0.01"
				on:mouseup={() => {
					paused = false;
				}}
				on:input={() => {
					paused = true;
					currentTime = duration * timelinePos;
				}}
			/>
			<button
				class="h-10 rounded-lg bg-blue-500 px-5 pb-1"
				on:click={() => {
					muted = !muted;
				}}
			>
				{muted ? 'muted' : 'unmuted'}
			</button>
			<Slider width={VOLUME_SLIDER_WIDTH} bind:value={volume} />
		</div>
	</div>

	{#if previewFlag === true}
		<video
			class="absolute left-0 top-0 h-[720px] max-w-fit"
			src={preview}
			bind:currentTime={preveiwCurrentTime}
			bind:paused={previewPaused}
			loop={true}
			autoplay={previewAutoPlay}
			on:click={() => {
				previewFlag = false;
				paused = false;
			}}
		>
			<track kind="captions" />
		</video>
	{/if}
</div>

<style>
	/* Firefox range input */
	input[type='range']::-moz-range-thumb {
		@apply h-4 w-4 rounded-full bg-white;
	}
	input[type='range']::-moz-range-track {
		@apply h-2 rounded-full bg-zinc-600;
	}
	input[type='range']::-moz-range-progress {
		@apply h-2 rounded-full bg-zinc-400;
	}

	/* Chrome range input */
	/* input[type='range']::-webkit-slider-thumb {
		@apply h-4 w-4 rounded-full bg-white;
	}
	input[type='range']::-webkit-slider-runnable-track {
		@apply h-2 rounded-full bg-zinc-600;
	} */
</style>
