<script lang="ts">
	export let styling = '';
	export let direction = '';
	export let position = '';
	export let animationStart = false;

	$: startPosition = position.toLowerCase() === 'rear' ? 'opacity-0' : '';
</script>

<!-- Animated by this div -->
<!-- pass in the styling as prop?? -->
<div
	class="h-fit w-fit {styling}"
	class:animate-moveOutLeft={direction.toLowerCase() === 'right' && animationStart}
	class:animate-moveOutRight={direction.toLowerCase() === 'left' && animationStart}
>
	<slot>
		<!-- Heading goes here -->
	</slot>
</div>

<style>
	.animate-moveOutLeft {
		animation: moveOutLeft 2000ms ease normal forwards;
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
		animation: moveOutRight 2000ms ease normal forwards;
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

	.animate-moveInLeft {
		animation: moveInLeft 2000ms ease normal forwards;
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
		animation: moveInRight 2000ms ease normal forwards;
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
