<script lang="ts">
	import Card from './Card.svelte';

	const dummyData = [
		{
			id: 50,
			date: '2023.05.19',
			heading: 'Heading',
			name: 'tom'
		},
		{
			id: 51,
			date: '2023.05.20',
			heading: 'Heading',
			name: 'karl'
		},
		{
			id: 52,
			date: '2023.05.21',
			heading: 'Heading',
			name: 'ion'
		},
		{
			id: 53,
			date: '2023.05.22',
			heading: 'Heading',
			name: 'brandon'
		}
	];
	let selected = dummyData[0];

	const SLIDE_WIDTH = 596 as const;
	const pageLimit = (dummyData.length - 1) * -1;

	let dragFlag = false;
	let clickBlock = false; // try to find better solution
	let scroll = 0;
	let referenceX = 0;

	let modalFlag = false;
	let animationIn = false;
	let animationOut = false;

	let page = 0;

	let test: HTMLElement;
</script>

<svelte:window
	on:mousemove={(e) => {
		if (dragFlag === false) return;
		else clickBlock = true;

		scroll += e.screenX - referenceX;
		referenceX = e.screenX;
	}}
	on:mouseup={(e) => {
		setTimeout(() => {
			clickBlock = false;
		}, 10);
		dragFlag = false;

		let page = Math.round(scroll / SLIDE_WIDTH);
		if (page > 0) {
			scroll = SLIDE_WIDTH * 0;
			return;
		}
		if (page < pageLimit) {
			scroll = SLIDE_WIDTH * pageLimit;
			return;
		}
		scroll = SLIDE_WIDTH * page;
	}}
/>

<main class="h-screen min-w-full overflow-x-hidden">
	<!-- <img class="w-full" src="social_coffee_house/fv_pc.png" alt="" /> -->
	<!-- <div class="pt-10"></div>
	<div class="mx-auto h-fit w-fit">
		<p>{`modalFlag : ${modalFlag}`}</p>
		<p>{`animationIn : ${animationIn}`}</p>
		<p>{`animationOut : ${animationOut}`}</p>
		<p>{`clickBlock : ${clickBlock}`}</p>
		<p>{`dragFlag : ${dragFlag} (scroll : ${scroll})`}</p>
	</div> -->

	<!-- js implementation -->
	<div class="pt-24"></div>
	<div
		class="flex h-[500px] w-screen items-center justify-center overflow-hidden border-y-2 border-[#003e59] bg-[#00a1c0]"
	>
		<div
			class="relative flex w-[--width] items-center justify-center"
			style:--width="{SLIDE_WIDTH}px"
		>
			<button
				class="absolute left-0 top-1/2"
				on:click={() => {
					page = scroll / SLIDE_WIDTH;
					if (page < 0) {
						scroll = (page + 1) * SLIDE_WIDTH;
					}
				}}
			>
				<img class="w-[18px]" src="social_coffee_house/arrow_left.png" alt="left arrow" />
			</button>
			<button
				class="absolute right-0 top-1/2"
				on:click={() => {
					page = scroll / SLIDE_WIDTH;
					if (page > pageLimit) {
						scroll = (page - 1) * SLIDE_WIDTH;
					}
				}}
			>
				<img class="w-[18px]" src="social_coffee_house/arrow_right.png" alt="right arrow" />
			</button>
			<ul
				class="flex h-fit w-[500px] translate-x-[--position] flex-row gap-24"
				class:transition-transform={!dragFlag}
				class:duration-500={!dragFlag}
				style:--position="{scroll}px"
			>
				{#each dummyData as card, index}
					{@const { id, date, heading, name } = card}
					<li>
						<button
							on:mousedown={(e) => {
								referenceX = e.screenX;
								dragFlag = true;
							}}
							on:click={() => {
								if (clickBlock === true) return;

								selected = dummyData[index];
								modalFlag = true;
								animationIn = true;
							}}
						>
							<Card {id} {date} {heading} {name}></Card>
						</button>
					</li>
				{/each}
			</ul>
		</div>
	</div>

	<!-- Tailwind scroll snap -->
	<!-- <div class="pt-10"></div>
	<div
		class="relative flex h-[500px] w-screen scroll-pl-5 items-center justify-center gap-24 overflow-hidden border-y-2 border-[#003e59] bg-[#00a1c0]"
	>
		<div class="relative flex h-full w-[--width]" style:--width="{SLIDE_WIDTH}px">
			<button
				class="absolute left-0 top-1/2 z-10"
				on:click={() => {
					test.scrollBy({ left: -SLIDE_WIDTH, behavior: 'smooth' });
					console.log(test.scrollLeft);
				}}
			>
				<img class="w-[18px]" src="social_coffee_house/arrow_left.png" alt="left arrow" />
			</button>
			<button
				class="absolute right-0 top-1/2 z-10"
				on:click={() => {
					test.scrollBy({ left: SLIDE_WIDTH, behavior: 'smooth' });
					console.log(test.scrollLeft);
				}}
			>
				<img class="w-[18px]" src="social_coffee_house/arrow_right.png" alt="right arrow" />
			</button>
		</div>
		<div
			class="absolute left-0 flex w-full snap-x snap-mandatory flex-row gap-24 overflow-x-scroll scroll-smooth [-ms-overflow-style:none] [scrollbar-width:none] [&::-webkit-scrollbar]:hidden"
			bind:this={test}
		>
			<div>
				<div class="w-[50vw]"></div>
			</div>
			{#each dummyData as card, index}
				{@const { id, date, heading, name } = card}
				<div class="snap-center">
					<Card {id} {date} {heading} {name}></Card>
				</div>
			{/each}
			<div>
				<div class="w-[50vw]"></div>
			</div>
		</div>
	</div> -->

	{#if modalFlag === true}
		{@const { id, date, heading, name } = selected}
		<button
			class="absolute left-0 top-0 flex h-screen w-screen items-center justify-center bg-black/50"
			class:modal-fadeIn={animationIn === true}
			class:modal-fadeOut={animationOut === true}
			on:click|stopPropagation={() => {
				animationIn = false;
				animationOut = true;
			}}
			on:animationend={() => {
				if (animationIn === true) {
					return;
				}

				animationOut = false;
				modalFlag = false;
			}}
		>
			<div class="h-fit w-fit">
				<div class="mx-auto mb-1 block h-fit w-fit">
					<button
						class="h-[50px] w-[50px] rounded-full border-2 border-[#003e59] bg-white text-[30px] text-[#003e59] drop-shadow-[-3px_3px_0px_#003e59]"
					>
						X
					</button>
				</div>
				<Card {id} {date} {heading} {name}></Card>
			</div>
		</button>
	{/if}

	<a
		class="fixed bottom-10 left-10 drop-shadow-[-3px_3px_0px_#003e59] transition-transform duration-500 hover:scale-110"
		href="https://socialcoffeehouse.arca.tokyo/"
	>
		<img class="h-[160px] w-[160px]" src="social_coffee_house/circle_center.png" alt="" />
		<div
			class="absolute left-0 top-0 flex h-full w-full animate-[spin_11s_linear_infinite] items-center justify-center"
		>
			<img class="h-[135px] w-[135px]" src="social_coffee_house/circle_txt.png" alt="" />
		</div>
	</a>
</main>

<style>
	.modal-fadeIn {
		animation: fadeIn 200ms ease normal forwards;
	}
	@keyframes fadeIn {
		0% {
			opacity: 0;
		}
		100% {
			opacity: 1;
		}
	}

	.modal-fadeOut {
		animation: fadeOut 200ms ease normal forwards;
	}
	@keyframes fadeOut {
		0% {
			opacity: 1;
		}
		100% {
			opacity: 0;
		}
	}
</style>
