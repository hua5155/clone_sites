<script lang="ts">
	import Card from './Card.svelte';

	let modalFlag = false;
	let animationIn = false;
	let animationOut = false;

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
	let clickBlock = false; // try to find better solution

	let scroll = 0;
	let referenceX = 0;
	let dragFlag = false;
	let slideElement: HTMLElement;
	const handleDrag = (e: MouseEvent) => {
		if (dragFlag === false) {
			return;
		}

		clickBlock = true;

		// let referenceX = slideElement.getBoundingClientRect().left;
		let deviation = e.pageX - referenceX;
		scroll += deviation;

		referenceX = e.pageX;
	};
</script>

<main class="absolute left-0 top-0 h-screen w-screen max-w-full">
	<div class="mx-auto mt-10 h-fit w-fit">
		<p>{`modalFlag : ${modalFlag}`}</p>
		<p>{`animationIn : ${animationIn}`}</p>
		<p>{`animationOut : ${animationOut}`}</p>
		<p>{`dragFlag : ${dragFlag} (scroll : ${scroll}), clickBlock : ${clickBlock}`}</p>
	</div>

	<div class="mt-10 border-b-2 border-t-2 border-[#003e59] bg-[#00a1c0]">
		<ul
			class="draggable mx-auto mt-10 flex h-[500px] w-[500px] flex-row space-x-24"
			style="--position: {scroll}px;"
			bind:this={slideElement}
		>
			{#each dummyData as card, index}
				<li
					on:mousedown={(e) => {
						// console.log('mouse down');
						referenceX = e.pageX;
						dragFlag = true;
					}}
				>
					<button
						class=""
						on:click={() => {
							if (clickBlock === true) {
								return;
							}
							selected = dummyData[index];
							modalFlag = true;
							animationIn = true;
						}}
					>
						<Card id={card.id} date={card.date} heading={card.heading}>
							<div class="flex flex-row space-x-5">
								<div class="flex flex-row space-x-1">
									<div class="h-[110px] w-[110px] border-2 border-[#003e59] bg-pink-400" />
									<div
										class="h-fit w-fit bg-[#ffde05] text-[20px] font-[400] capitalize leading-[1.6rem] text-[#003e59]"
									>
										{card.name}
									</div>
								</div>
							</div>
						</Card>
					</button>
				</li>
			{/each}
		</ul>
	</div>

	{#if modalFlag === true}
		<div
			class="absolute left-0 top-0 flex h-screen w-screen items-center justify-center bg-black/50"
			class:modal-fadeIn={animationIn === true}
			class:modal-fadeOut={animationOut === true}
			on:click|stopPropagation={() => {
				animationIn = false;
				animationOut = true;
			}}
			on:keydown={() => {}}
			on:animationend={() => {
				if (animationIn === true) {
					return;
				}

				animationOut = false;
				modalFlag = false;
			}}
		>
			<div class="h-fit w-fit">
				<button class="mx-auto mb-1 block h-fit w-fit">
					<div
						class="box-shadow h-[50px] w-[50px] rounded-full border-2 border-[#003e59] bg-white text-[30px] text-[#003e59]"
					>
						X
					</div>
				</button>
				<Card id={selected.id} date={selected.date} heading={selected.heading}>
					<div class="flex flex-row space-x-5">
						<div class="flex flex-row space-x-1">
							<div class="h-[110px] w-[110px] border-2 border-[#003e59] bg-pink-400" />
							<div
								class="h-fit w-fit bg-[#ffde05] text-[20px] font-[400] capitalize leading-[1.6rem] text-[#003e59]"
							>
								{selected.name}
							</div>
						</div>
					</div>
				</Card>
			</div>
		</div>
	{/if}

	<div
		class="box-shadow fixed bottom-10 left-10 h-fit w-fit transition-transform duration-500 hover:scale-110"
	>
		<div class="z-0 h-fit w-fit">
			<img class="h-[160px] w-[160px]" src="social_coffee_house/circle_center.png" alt="" />
		</div>
		<div class="rotate absolute left-0 top-0 z-10 flex h-full w-full items-center justify-center">
			<img class="h-[135px] w-[135px]" src="social_coffee_house/circle_txt.png" alt="" />
		</div>
	</div>
</main>

<svelte:window
	on:keypress={(e) => {
		// console.log(`window : ${e.key}`);
	}}
	on:mousemove={(e) => {
		// console.log('mouse move');
		handleDrag(e);
	}}
	on:mouseup={() => {
		// console.log('mouse up');
		setTimeout(() => {
			clickBlock = false;
		}, 10);
		dragFlag = false;
	}}
/>

<style>
	.box-shadow {
		filter: drop-shadow(-3px 3px 0px #003e59);
	}

	.rotate {
		animation: rotate 11000ms linear infinite;
	}
	@keyframes rotate {
		0% {
			transform: rotate(0deg);
		}
		100% {
			transform: rotate(360deg);
		}
	}

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

	.slide {
		transform: translateX();
	}
	.draggable {
		transform: translateX(var(--position));
	}
</style>
