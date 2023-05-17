<script lang="ts">
	import VideoPlayer from '$lib/component/Chanel/When_coco_meets_chanel/VideoPlayer.svelte';

	let slides = ['coco', 'mademoiselle', 'gabrielle_chanel', 'coco_by_karl'];

	let page = 0;
	const maxPage = 3;
	let direction = 'right';

	const leftCheck = (index: number, page: number) => {
		if (page === 0) {
			return index === maxPage ? true : false;
		}
		return index === page - 1 ? true : false;
	};
	const rightCheck = (index: number, page: number) => {
		if (page === maxPage) {
			return index === 0 ? true : false;
		}
		return index === page + 1 ? true : false;
	};
	const outerCheck = (index: number, page: number) => {
		let outer = page;
		if (direction === 'left') {
			outer += 2;
			if (outer > maxPage) {
				outer -= maxPage + 1;
			}
			if (index === outer) {
				return true;
			}
		} else if (direction === 'right') {
			if (outer < 2) {
				outer += maxPage + 1;
			}
			outer -= 2;
			if (index === outer) {
				return true;
			}
		}

		return false;

		/*
    page -> index
    0 -> 3, 2
    1 -> 4, 3
    2 -> 0, 4
    3 -> 1, 0
    4 -> 2, 1
    */
	};
	const hiddenCheck = (index: number, page: number) => {
		if (
			index != page &&
			!leftCheck(index, page) &&
			!rightCheck(index, page) &&
			!outerCheck(index, page)
		) {
			return true;
		}
		return false;
	};
</script>

<div class="h-[1353px] w-full bg-zinc-800 text-white">
	<h2 class="py-[72px] text-center text-[40px] font-[600] leading-[45px]">當 COCO 邂逅香奈兒</h2>

	<div class="relative mx-auto h-[720px] w-[1280px]">
		{#each slides as slide, index}
			<div
				class="absolute top-0"
				class:left-outer-slide={outerCheck(index, page) && direction === 'left'}
				class:left-slide={leftCheck(index, page)}
				class:middle-slide={index === page}
				class:right-slide={rightCheck(index, page)}
				class:right-outer-slide={outerCheck(index, page) && direction === 'right'}
				class:hidden-slide={hiddenCheck(index, page)}
			>
				<VideoPlayer {slide} selected={index === page} />
			</div>
		{/each}
	</div>

	<div class="mx-auto mt-10 flex h-fit w-fit flex-row space-x-5">
		<button
			class="h-10 rounded-lg bg-blue-500 px-5 pb-1"
			on:click={() => {
				direction = 'left';
				if (page === 0) {
					page = maxPage;
				} else {
					page -= 1;
				}
			}}
		>
			{`Left`}
		</button>
		<p>{`${page + 1} / ${maxPage + 1}`}</p>
		<button
			class="h-10 rounded-lg bg-blue-500 px-5 pb-1"
			on:click={() => {
				direction = 'right';
				if (page === maxPage) {
					page = 0;
				} else {
					page += 1;
				}
			}}
		>
			{`Right`}
		</button>
	</div>
</div>

<style>
	.left-outer-slide {
		transform: translateX(-250%);
	}
	.left-slide {
		transform: translateX(-125%);
	}
	.middle-slide {
		transform: translateX(0%);
	}
	.right-slide {
		transform: translateX(125%);
	}
	.right-outer-slide {
		transform: translateX(250%);
	}
	.hidden-slide {
		display: none;
	}

	.slide-transition {
		transition-property: left;
		transition-timing-function: ease;
		transition-duration: 1000ms;
	}
</style>
