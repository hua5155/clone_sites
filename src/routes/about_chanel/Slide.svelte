<script lang="ts">
	import Slide, {
		direction,
		animationStart,
		frontIndex,
		backIndex
	} from '$lib/component/Chanel/About_Chanel/Slide.svelte';

	let page = 0;
	const maxPage = 9;
	let slideHeight = 730;

	const handlePage = () => {
		if ($animationStart === true) {
			return;
		}

		// console.log(`handlePage : ${direction}`); // debug

		if ($direction === 'Left') {
			if (page === 0) {
				page = maxPage;
			} else {
				page -= 1;
			}
		}
		if ($direction === 'Right') {
			if (page === maxPage) {
				page = 0;
			} else {
				page += 1;
			}
		}

		$backIndex = page;
		$animationStart = true;
		setTimeout(() => {
			$frontIndex = $backIndex;
			$animationStart = false;
		}, 2000);
	};
</script>

<div
	class="relative w-full bg-zinc-800 py-10 text-white transition-all duration-1000"
	style:height="{slideHeight + 308}px"
>
	<h2 class="text-center text-[40px] font-[600]">關於 COCO 香奈兒</h2>

	<div class="mx-auto mt-20 flex w-[1600px] flex-row justify-between space-x-1">
		<!-- Left button -->
		<div class="w-[240px] bg-sky-500/50">
			<button
				class="mx-auto mt-[350px] w-full text-center"
				on:click={() => {
					$direction = 'Left';
					handlePage();
				}}
			>
				Left
			</button>
		</div>

		<div class="h-fit w-full" bind:clientHeight={slideHeight}>
			<Slide />
		</div>

		<!-- Right button -->
		<div class="w-[240px] bg-sky-500/50">
			<button
				class="mx-auto mt-[350px] w-full text-center"
				on:click={() => {
					$direction = 'Right';
					handlePage();
				}}
			>
				Right
			</button>
		</div>
	</div>

	<div class="absolute bottom-10 mt-16 w-full">
		<p class="text-center">{`${page + 1} / ${maxPage + 1}`}</p>
	</div>
</div>

<style>
</style>
