<script lang="ts">
	import Card from './Card.svelte';

	let modalFlag = false;
	let animationIn = false;
	let animationOut = false;
</script>

<main class="absolute left-0 top-0 h-screen w-screen max-w-full">
	<div class="mx-auto mt-10 h-fit w-fit">
		<p>
			{`modalFlag : ${modalFlag}`}
		</p>
		<p>
			{`animationIn : ${animationIn}`}
		</p>
		<p>
			{`animationOut : ${animationOut}`}
		</p>
	</div>

	<div class="mx-auto mt-10 h-fit w-fit">
		<button
			class=""
			on:click={() => {
				modalFlag = true;
				animationIn = true;
			}}
		>
			<Card id={50} date="2023.05.19" heading="Heading">
				<div class="flex flex-row space-x-5">
					<div class="flex flex-row space-x-1">
						<div class="h-[110px] w-[110px] border-2 border-[#003e59] bg-pink-400" />
						<div
							class="h-fit w-fit bg-[#ffde05] text-[20px] font-[400] leading-[1.6rem] text-[#003e59]"
						>
							Guest name
						</div>
					</div>
				</div>
			</Card>
		</button>
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
				<Card id={50} date="2023.05.19" heading="Heading">
					<div class="flex flex-row space-x-5">
						<div class="flex flex-row space-x-1">
							<div class="h-[110px] w-[110px] border-2 border-[#003e59] bg-pink-400" />
							<div
								class="h-fit w-fit bg-[#ffde05] text-[20px] font-[400] leading-[1.6rem] text-[#003e59]"
							>
								Guest name
							</div>
						</div>
					</div>
				</Card>
			</div>
		</div>
	{/if}
</main>

<svelte:window
	on:keypress={(e) => {
		console.log(`window : ${e.key}`);
	}}
/>

<style>
	.box-shadow {
		filter: drop-shadow(-3px 3px 0px #003e59);
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
</style>
