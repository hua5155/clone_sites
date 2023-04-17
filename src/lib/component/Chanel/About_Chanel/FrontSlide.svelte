<script lang="ts">
	import { direction, animationStart } from './Slide.svelte';

	export let imgSrc = '';
	export let imgAlt = '';
	export let headingPos = '';

	let imgHeight = 0;
</script>

<!-- Whole slide container -->
<div class="absolute left-0 top-0 flex w-full flex-row">
	<div class="w-[541px]" style:height="{imgHeight}px">
		<div
			class="z-30 h-fit w-fit {headingPos}"
			class:animate-moveOutLeft={$direction.toLowerCase() === 'right' && $animationStart}
			class:animate-moveOutRight={$direction.toLowerCase() === 'left' && $animationStart}
			style:--duration="1000ms"
		>
			<slot name="heading" />
		</div>
	</div>
	<div
		class="absolute z-10 w-[541px] overflow-hidden"
		class:animate-shrinkLeft={$direction.toLowerCase() === 'right' && $animationStart}
		class:animate-shrinkRight={$direction.toLowerCase() === 'left' && $animationStart}
		style:height="{imgHeight}px"
		on:animationend={() => {
			// animationStart = false;
		}}
	>
		<div
			class="absolute h-fit w-fit {$direction === 'left' ? 'right-0' : ''}"
			bind:clientHeight={imgHeight}
		>
			<img
				class="w-[541px] max-w-[541px]"
				class:animate-zoomIn={$animationStart}
				src={imgSrc}
				alt={imgAlt}
			/>
		</div>
	</div>

	<div
		class="relative z-30"
		class:animate-moveOutLeft={$direction.toLowerCase() === 'right' && $animationStart}
		class:animate-moveOutRight={$direction.toLowerCase() === 'left' && $animationStart}
		style:--duration="1500ms"
	>
		<slot name="quote" />
	</div>
	<!-- <slot> -->
	<!-- Slide goes here -->
	<!-- </slot> -->
</div>

<style>
	.animate-zoomIn {
		animation: zoomIn 2000ms ease normal forwards;
	}
	@keyframes zoomIn {
		0% {
		}
		100% {
			transform: scale(1.5);
		}
	}

	.animate-shrinkLeft {
		animation: shrinkLeft 1000ms ease normal forwards;
	}
	@keyframes shrinkLeft {
		0% {
			width: 541px;
		}
		100% {
			width: 0px;
		}
	}

	.animate-shrinkRight {
		animation: shrinkRight 1000ms ease normal forwards;
	}
	@keyframes shrinkRight {
		0% {
			width: 541px;
			margin-left: 0px;
		}
		100% {
			width: 0px;
			margin-left: 541px;
		}
	}

	.animate-moveOutLeft {
		animation: moveOutLeft var(--duration) ease normal forwards;
	}
	@keyframes moveOutLeft {
		0% {
		}
		50% {
			opacity: 0;
		}
		100% {
			transform: translateX(-541px);
			opacity: 0;
		}
	}

	.animate-moveOutRight {
		animation: moveOutRight var(--duration) ease normal forwards;
	}
	@keyframes moveOutRight {
		0% {
		}
		50% {
			opacity: 0;
		}
		100% {
			transform: translateX(541px);
			opacity: 0;
		}
	}
</style>
