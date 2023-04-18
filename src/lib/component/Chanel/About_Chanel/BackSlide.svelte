<script lang="ts">
	import { direction, animationStart } from './Slide.svelte';

	export let imgSrc = '';
	export let imgAlt = '';
	export let headingPos = '';

	let imgHeight = 0;
</script>

<!-- Whole slide container -->
<div class="relative flex w-full flex-row">
	<div class="w-[541px]" style:height="{imgHeight}px">
		<div
			class="z-30 h-fit w-fit opacity-0 {headingPos}"
			class:animate-moveInRight={$direction.toLowerCase() === 'right' && $animationStart}
			class:animate-moveInLeft={$direction.toLowerCase() === 'left' && $animationStart}
			style:--duration="1000ms"
		>
			<slot name="heading" />
		</div>
	</div>
	<div
		class="absolute z-10 w-[541px] overflow-hidden"
		class:animate-appearRight={$direction.toLowerCase() === 'right' && $animationStart}
		class:animate-appearLeft={$direction.toLowerCase() === 'left' && $animationStart}
		style:height="{imgHeight}px"
		style:width="0px"
		on:animationend={() => {
			// animationStart = false;
		}}
	>
		<div
			class="absolute h-fit w-fit {$direction.toLowerCase() === 'right' ? 'right-0' : ''}"
			bind:clientHeight={imgHeight}
		>
			<img
				class="w-[541px] max-w-[541px]"
				class:animate-zoomOut={$animationStart}
				src={imgSrc}
				alt={imgAlt}
			/>
		</div>
	</div>

	<div
		class="relative z-30 opacity-0"
		class:animate-moveInRight={$direction.toLowerCase() === 'right' && $animationStart}
		class:animate-moveInLeft={$direction.toLowerCase() === 'left' && $animationStart}
		style:--duration="1500ms"
	>
		<slot name="quote" />
	</div>
	<!-- <slot> -->
	<!-- Slide goes here -->
	<!-- </slot> -->
</div>

<style>
	.animate-zoomOut {
		animation: zoomOut 2000ms ease;
	}
	@keyframes zoomOut {
		0% {
			transform: scale(1.5);
		}
		100% {
			transform: scale(1);
		}
	}

	.animate-appearLeft {
		animation: appearLeft 1000ms ease 200ms normal forwards;
	}
	@keyframes appearLeft {
		0% {
			width: 0px;
		}
		100% {
			width: 541px;
		}
	}

	.animate-appearRight {
		animation: appearRight 1000ms ease 200ms normal forwards;
	}
	@keyframes appearRight {
		0% {
			width: 0px;
			margin-left: 541px;
		}
		100% {
			width: 541px;
			margin-left: 0px;
		}
	}

	.animate-moveInLeft {
		animation: moveInLeft var(--duration) ease 200ms normal forwards;
	}
	@keyframes moveInLeft {
		0% {
			transform: translateX(-541px);
		}
		50% {
			opacity: 1;
		}
		100% {
			transform: translateX(0px);
			opacity: 1;
		}
	}

	.animate-moveInRight {
		animation: moveInRight var(--duration) ease 200ms normal forwards;
	}
	@keyframes moveInRight {
		0% {
			transform: translateX(541px);
		}
		50% {
			opacity: 1;
		}
		100% {
			transform: translateX(0px);
			opacity: 1;
		}
	}
</style>
