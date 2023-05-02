<script lang="ts">
	let images = [
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
	];

	let page = 0;
	const maxPage = 10;
	let collapse = false;

	const leftCheck = (index: number, page: number) => {
		if (page === 0) {
			return index === 10 ? true : false;
		}
		return index === page - 1 ? true : false;
	};
	const rightCheck = (index: number, page: number) => {
		if (page === maxPage) {
			return index === 0 ? true : false;
		}
		return index === page + 1 ? true : false;
	};
	const hiddenCheck = (index: number, page: number) => {
		if (index != page && !leftCheck(index, page) && !rightCheck(index, page)) {
			return true;
		}
		return false;
	};
	const handleClick = (index: number) => {
		if (index === 0) {
			collapse = false;
		}

		if (collapse === true) {
			return;
		}

		if (leftCheck(index, page)) {
			page = page === 0 ? maxPage : page - 1;
		}
		if (rightCheck(index, page)) {
			page = page === maxPage ? 0 : page + 1;
		}
	};
</script>

<div class="h-[1323px] w-full bg-white text-black">
	<h2 class="py-[72px] text-center text-[40px] font-[600] leading-[45px]">
		藝術家眼中的 COCO 香奈兒
	</h2>

	<!-- Arts container -->
	<div class="relative mx-auto h-[819px] w-[1599px]">
		<!-- Individual arts -->
		{#each images as image, index}
			<div
				class="absolute flex h-[819px] w-[533px] items-center justify-center transition-all duration-1000"
				class:left-image={leftCheck(index, page) && !collapse}
				class:middle-image={index === page}
				class:right-image={rightCheck(index, page) && !collapse}
				class:hidden-image={hiddenCheck(index, page)}
				class:left-collapse={leftCheck(index, page) && collapse}
				class:right-collapse={rightCheck(index, page) && collapse}
				on:click={() => {
					handleClick(index);
				}}
				on:keydown
			>
				<img
					class="max-h-[819px] max-w-[533px] transition-all duration-1000"
					class:selected={index === page}
					class:not-selected={index != page}
					src={image}
					alt=""
				/>
			</div>
		{/each}
	</div>

	<div class="mx-auto h-fit w-fit">
		<select class="h-10 px-5" bind:value={page}>
			{#each images as image, index}
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
				page = 0;
			}}>collapse</button
		>
	</div>
</div>

<style>
	/* div position */
	.left-image {
		left: 0px;
		z-index: 10;
	}
	.right-image {
		left: 1066px;
		z-index: 10;
	}
	.middle-image {
		left: 533px;
		z-index: 20;
	}
	.hidden-image {
		left: 533px;
		z-index: 0;
		scale: 0;
		opacity: 0;
	}
	.left-collapse {
		left: 240px;
		z-index: 10;
	}
	.right-collapse {
		left: 826px;
		z-index: 10;
	}

	/* img scaling */
	.selected {
		/* max-width: 533px; */
		scale: 1;
	}
	.not-selected {
		/* max-width: 426px; */
		scale: 0.8;
	}
</style>
