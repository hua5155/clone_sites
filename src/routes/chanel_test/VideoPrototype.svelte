<script lang="ts">
	import Slider from '$lib/component/Input/Slider.svelte';

	let duration: number;
	let currentTime = 0;
	let paused = true;
	let volume = 1;
	let muted = false;

	let previewFlag = true;

	let playState = false;

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
		class="z-0"
		src="Chanel/Video/coco/main.mp4"
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
			class="absolute left-0 top-0 z-20"
			src="Chanel/Video/coco/preview.mp4"
			loop={true}
			autoplay={true}
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

<div class="bg-gray-500 p-5">
	<p>
		{`time : ${currentTime}/${duration} (${percentage})`} <br />
		{`paused : ${paused}`} <br />
		{`muted : ${muted}`} <br />
		{`volume : ${volume}`} <br />
		{`playState : ${playState}`}
	</p>
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
