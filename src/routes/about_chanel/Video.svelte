<script lang="ts">
	import VideoPlayer from '$lib/component/Chanel/When_coco_meets_chanel/VideoPlayer.svelte';
	import { onMount } from 'svelte';

	function isLeft(index: number, currPage: number) {
		if (currPage === 0) {
			if (index === MAX_INDEX) return true;
			return false;
		}
		if (index === currPage - 1) return true;
		return false;
	}
	function isRight(index: number, currPage: number) {
		if (currPage === MAX_INDEX) {
			if (index === 0) return true;
			return false;
		}
		if (index === currPage + 1) return true;
		return false;
	}
	function getOuterRight(currPage: number) {
		let outer = currPage;
		outer += 2;
		if (outer > MAX_INDEX) {
			outer -= MAX_INDEX + 1;
		}
		return outer;
	}
	function getOuterLeft(currPage: number) {
		let outer = currPage;
		if (outer < 2) {
			outer += MAX_INDEX + 1;
		}
		outer -= 2;

		return outer;
	}

	const SLIDES = ['coco', 'mademoiselle', 'gabrielle_chanel', 'coco_by_karl'] as const;
	// const SLIDES = [1, 2, 3, 4, 5];
	let currPage = 0;
	const MAX_INDEX = 3 as const;

	let pause = true;

	onMount(() => {
		SLIDES.forEach((value, index) => {
			if (index === currPage) {
				document.getElementById(`video-${index}`)?.style.setProperty('--position', '0%');
				return;
			}
			if (index === MAX_INDEX) {
				document.getElementById(`video-${index}`)?.style.setProperty('--position', '-125%');
				return;
			}
			if (index === currPage + 1) {
				document.getElementById(`video-${index}`)?.style.setProperty('--position', '125%');
				return;
			}
			document.getElementById(`video-${index}`)?.style.setProperty('--position', '250%');
		});
	});
</script>

<div class="flex h-[1353px] w-full flex-col items-center overflow-x-hidden bg-zinc-800 text-white">
	<h2 class="py-[72px] text-center text-[40px] font-[600] leading-[45px]">當 COCO 邂逅香奈兒</h2>

	<div class="relative h-[720px] w-[1280px]">
		{#each SLIDES as slide, index}
			<div
				class="absolute top-0 translate-x-[--position] transform-gpu duration-1000 ease-in-out"
				class:transition-none={true}
				id={`video-${index}`}
			>
				<VideoPlayer {slide} selected={index === currPage} />
				<!-- MARK: prototype div works but VideoPlayer doesn't... -->
				<!-- <div
					class="flex aspect-video w-[200px] items-center justify-center bg-gray-500/50 text-9xl text-white"
				>
					<p class="w-full text-center">{index + 1}</p>
				</div> -->
			</div>
		{/each}
	</div>

	<div class="flex h-fit w-fit flex-row items-center space-x-5 pt-10">
		<button
			class="h-10 rounded-lg bg-blue-500 px-5 pb-1"
			on:click={() => {
				let outerLeft = getOuterLeft(currPage);
				pause = true;
				document.getElementById(`video-${outerLeft}`)?.style.setProperty('--position', '-250%');
				setTimeout(() => {
					pause = false;
					document.getElementById(`video-${outerLeft}`)?.style.setProperty('--position', '-125%');
					SLIDES.forEach((value, index) => {
						if (index === currPage) {
							document.getElementById(`video-${index}`)?.style.setProperty('--position', '125%');
						}
						if (isLeft(index, currPage)) {
							document.getElementById(`video-${index}`)?.style.setProperty('--position', '0%');
						}
						if (isRight(index, currPage)) {
							document.getElementById(`video-${index}`)?.style.setProperty('--position', '250%');
						}
					});
					if (currPage === 0) {
						currPage = MAX_INDEX;
					} else {
						currPage -= 1;
					}
				}, 1);
			}}
		>
			Left
		</button>
		<p>{`${currPage + 1} / ${MAX_INDEX + 1}`}</p>
		<button
			class="h-10 rounded-lg bg-blue-500 px-5 pb-1"
			on:click={() => {
				let outerRight = getOuterRight(currPage);
				pause = true;
				document.getElementById(`video-${outerRight}`)?.style.setProperty('--position', '250%');
				setTimeout(() => {
					pause = false;
					document.getElementById(`video-${outerRight}`)?.style.setProperty('--position', '125%');
					SLIDES.forEach((value, index) => {
						if (index === currPage) {
							document.getElementById(`video-${index}`)?.style.setProperty('--position', '-125%');
						}
						if (isLeft(index, currPage)) {
							document.getElementById(`video-${index}`)?.style.setProperty('--position', '-250%');
						}
						if (isRight(index, currPage)) {
							document.getElementById(`video-${index}`)?.style.setProperty('--position', '0%');
						}
					});
					if (currPage === MAX_INDEX) {
						currPage = 0;
					} else {
						currPage += 1;
					}
				}, 1);
			}}
		>
			Right
		</button>
	</div>
</div>

<style>
</style>
