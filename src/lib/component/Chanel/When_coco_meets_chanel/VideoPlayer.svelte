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

	let timelineAdjusting = false;
	let timelineLength = 320;
	let timelinePos = 0;
	$: percentage = currentTime / duration;
	$: currentTime = duration * (timelinePos / timelineLength);
	$: moveTimeline(percentage);
	$: if (playState === true) {
		paused = timelineAdjusting;
	}

	const moveTimeline = (percentage: number) => {
		timelinePos = timelineLength * percentage;
	};

	let volumeLength = 100;
	let volumePos = 100;
	$: volume = 1 * (volumePos / volumeLength);

	let hoverFlag = false;
</script>

<div
	class="relative h-fit w-fit overflow-hidden"
	on:focus={() => {}}
	on:mouseover={() => {
		hoverFlag = true;
	}}
	on:mouseout={() => {
		hoverFlag = false;
	}}
	on:blur={() => {}}
>
	<video
		class="z-0 h-[720px] max-w-fit"
		src={video}
		bind:currentTime
		bind:duration
		bind:paused
		bind:volume
		bind:muted
	>
		<track kind="captions" />
	</video>

	{#if previewFlag === true}
		<video
			class="absolute left-0 top-0 z-20 h-[720px] max-w-fit"
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

	<div class="absolute bottom-5 z-10 w-full">
		<div
			class="mx-auto flex h-fit w-fit flex-row items-center justify-center space-x-5 rounded-lg bg-zinc-800/80 px-7 py-5"
			class:animate-slideUp={hoverFlag}
			class:animate-slideDown={!hoverFlag}
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
			<Slider
				bind:sliderLength={timelineLength}
				bind:sliderPos={timelinePos}
				bind:adjusting={timelineAdjusting}
				primaryColor="bg-zinc-600"
				secondaryColor="bg-zinc-400"
				knobColor="bg-white"
			/>
			<button
				class="h-10 rounded-lg bg-blue-500 px-5 pb-1"
				on:click={() => {
					muted = !muted;
				}}
			>
				{muted ? 'muted' : 'unmuted'}
			</button>
			<Slider
				bind:sliderLength={volumeLength}
				bind:sliderPos={volumePos}
				primaryColor="bg-zinc-600"
				secondaryColor="bg-zinc-400"
				knobColor="bg-white"
			/>
		</div>
	</div>
</div>

<style>
	.animate-slideUp {
		animation: slideUp 500ms ease forwards;
	}
	@keyframes slideUp {
		0% {
			opacity: 0;
			transform: translateY(100%);
		}
		100% {
			opacity: 1;
			transform: translateY(0%);
		}
	}

	.animate-slideDown {
		animation: slideDown 500ms ease forwards;
	}
	@keyframes slideDown {
		0% {
			opacity: 1;
			transform: translateY(0%);
		}
		100% {
			opacity: 0;
			transform: translateY(100%);
		}
	}
</style>
