<script lang="ts">
	export let styling = '';
	export let direction = '';
	export let animationStart = false;
</script>

<!-- Animated by this div -->
<!-- pass in the styling as prop?? -->
<div
	class="h-fit {styling}"
	class:animate-moveLeft={direction.toLowerCase() === 'right' && animationStart}
	class:animate-moveRight={direction.toLowerCase() === 'left' && animationStart}
>
	<slot>
		<!-- Heading goes here -->
	</slot>
</div>

<style>
	.animate-moveLeft {
		animation: moveLeft 2000ms ease normal forwards;
	}
	@keyframes moveLeft {
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
	.animate-moveRight {
		animation: moveRight 2000ms ease normal forwards;
	}
	@keyframes moveRight {
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
