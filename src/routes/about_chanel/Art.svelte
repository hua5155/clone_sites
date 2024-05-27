<script lang="ts">
	const IMAGES = [
		'Chanel/Art/Horst_P._Horst_1937.webp',
		'Chanel/Art/marie_laurencin_1923.webp',
		'Chanel/Art/jean_cocteau_1937.webp',
		'Chanel/Art/man_ray_1935.webp',
		'Chanel/Art/cassandre_1942.webp',
		'Chanel/Art/christian_berard_1937.webp',
		'Chanel/Art/robert_doisneau_1953.webp',
		'Chanel/Art/cecil_beaton.webp',
		'Chanel/Art/christian_berard_1930.webp',
		'Chanel/Art/george_hoyningen-huene_1939.webp',
		'Chanel/Art/kees_van_dongen_1940.webp'
	] as const;

	let currPage = 0;
	const MAX_PAGE = 10 as const;
	let collapse = true;

	function isLeft(index: number, currPage: number) {
		if (currPage === 0) {
			if (index === MAX_PAGE) return true;
			return false;
		}
		if (index === currPage - 1) return true;
		return false;
	}
	function isRight(index: number, currPage: number) {
		if (currPage === MAX_PAGE) {
			if (index === 0) return true;
			return false;
		}
		if (index === currPage + 1) return true;
		return false;
	}
	function isHidden(index: number, currPage: number) {
		if (index !== currPage && !isLeft(index, currPage) && !isRight(index, currPage)) {
			return true;
		}
		return false;
	}
</script>

<div class="flex h-[1323px] w-full flex-col items-center bg-white text-black">
	<h2 class="py-[72px] text-center text-[40px] font-[600] leading-[45px]">
		藝術家眼中的 COCO 香奈兒
	</h2>

	<!-- Arts container -->
	<div class="relative h-[819px] w-[1599px]">
		<!-- Individual arts -->
		{#each IMAGES as image, index}
			<button
				class="absolute left-1/3 z-20 flex h-full w-1/3 scale-100 transform-gpu items-center justify-center opacity-100 transition-all duration-1000"
				class:left-expand={isLeft(index, currPage) && !collapse}
				class:right-expand={isRight(index, currPage) && !collapse}
				class:left-collapse={isLeft(index, currPage) && collapse}
				class:right-collapse={isRight(index, currPage) && collapse}
				class:hidden-image={isHidden(index, currPage)}
				on:click={() => {
					if (collapse === true) {
						collapse = false;
						return;
					}

					if (isLeft(index, currPage)) {
						if (currPage === 0) {
							currPage = MAX_PAGE;
							return;
						}
						currPage -= 1;
					}

					if (isRight(index, currPage)) {
						if (currPage === MAX_PAGE) {
							currPage = 0;
							return;
						}
						currPage += 1;
					}
				}}
			>
				<img
					class="max-h-[819px] max-w-[533px] scale-100 transform-gpu transition-all duration-1000"
					class:scale-[0.8]={index !== currPage}
					src={image}
					alt=""
				/>
			</button>
		{/each}
	</div>

	<div class=" h-fit w-fit">
		<select class="h-10 px-5" bind:value={currPage}>
			{#each IMAGES as image, index}
				<option value={index}>{index}</option>
			{/each}
		</select>
		<button
			class="h-10 rounded-lg bg-blue-500 px-5 pb-1"
			on:click={() => {
				collapse = false;
			}}>expand</button
		>
		<button
			class="h-10 rounded-lg bg-blue-500 px-5 pb-1"
			on:click={() => {
				collapse = true;
				currPage = 0;
			}}>collapse</button
		>
	</div>
</div>

<style>
	/* img position */
	.left-expand {
		@apply left-0 z-10;
	}
	.right-expand {
		@apply left-2/3 z-10;
	}
	.hidden-image {
		@apply left-1/3 z-0 scale-0 opacity-0;
	}
	.left-collapse {
		@apply left-[240px] z-10;
	}
	.right-collapse {
		@apply left-[826px] z-10;
	}
</style>
