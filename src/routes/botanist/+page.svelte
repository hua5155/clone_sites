<script lang="ts">
	import Bloom from './Bloom.svelte';
	import NavElement from './NavElement.svelte';

	const nav = ['FEATURE', ['SHAMPOO&TREATMENT', 'OUR BATH', 'BODY SOAP'], 'PRODUCTS'];
	let navFlag = false;
	let animationIn = false;
	let animationOut = false;
</script>

<main class="absolute left-0 top-0 h-screen w-screen max-w-full">
	<div class="h-screen w-screen px-[12px] pb-[60px] pt-[30px] md:px-[110px] md:py-[80px]">
		<div class="relative h-full w-full">
			<div
				class="animate-rotateUp absolute left-0 top-0 h-full w-full bg-[#DC94B8] [--opacity-end:0.2] [--rotate-end:-3deg] [--rotate-start:-30deg] [transform-origin:center]"
			/>
			<div
				class="animate-rotateUp absolute left-0 top-0 h-full w-full bg-[#DC94B8] [--rotate-start:-30deg] [transform-origin:center] [--opacity-end:0.4] [--rotate-end:-6deg]"
			/>
			<div
				class="animate-rotateUp relative h-full w-full bg-[url('botanist/img/kv_sp.jpg')] bg-cover bg-center [--opacity-end:1] [--rotate-end:0deg] [--rotate-start:30deg] [animation-delay:300ms] [transform-origin:left] md:bg-[url('botanist/img/kv.jpg')]"
			/>
			<div
				class="absolute left-0 top-0 flex h-full w-full flex-col items-center justify-between px-[max(28px,_7.46667%)] py-[max(40px,_10.66667%)] md:items-start md:p-[60px]"
			>
				<img class="w-[70px] md:w-fit" src="botanist/svg/logo-w.svg" alt="" />
				<Bloom />
			</div>
		</div>
	</div>

	<!-- Desktop nav bar -->
	<nav
		class="fixed right-8 top-[40%] z-50 hidden flex-col items-end text-[14px] font-[500] leading-[23px] tracking-[0.08rem] text-[#dd7994] md:flex"
	>
		<ul class="text-right">
			{#each nav as url}
				<NavElement {url} />
			{/each}
		</ul>
		<div
			class="group mt-7 flex h-[50px] w-fit items-center rounded-full bg-[#dd7994] px-5 text-[14px] font-[700] leading-[1] text-white transition-colors duration-300 hover:bg-[#520A4E]"
		>
			<div class="flex h-[14px] w-fit flex-col overflow-hidden">
				<span class="transition-transform duration-300 group-hover:-translate-y-full">CAMPAIGN</span
				>
				<span class="transition-transform duration-300 group-hover:-translate-y-full">CAMPAIGN</span
				>
			</div>
		</div>
	</nav>
	<!-- Mobile nav bar -->
	{#if navFlag === true}
		<div
			class="absolute left-0 top-0 h-screen w-screen bg-[url('botanist/img/bg.jpg')] bg-cover bg-right-top px-[13%] py-[70px] md:hidden"
			class:animate-fadeIn={animationIn === true}
			class:animate-fadeOut={animationOut === true}
			on:animationend={() => {
				if (animationIn === true) {
					return;
				}

				animationOut = false;
				navFlag = false;
			}}
		>
			<div
				class:animate-slideUp={animationIn === true}
				class:animate-slideDown={animationOut === true}
			>
				<div class="mx-auto mb-16 h-fit w-fit">
					<img src="botanist/svg/logo-bk.svg" alt="" />
				</div>
				<ul
					class="text-left text-[18px] font-[500] leading-[1.2] tracking-[0.08rem] text-[#dd7994]"
				>
					{#each nav as url}
						<NavElement {url} />
					{/each}
				</ul>
			</div>
		</div>
	{/if}
	<button
		class="fixed bottom-5 right-0 z-50 md:hidden"
		on:click={() => {
			animationIn = navFlag === false ? true : false;
			animationOut = navFlag === true ? true : false;

			if (animationOut === true) {
				return;
			}

			navFlag = !navFlag;
		}}
	>
		<div class="h-16 w-12 rounded-l-full bg-[#520A4E] px-5 py-2">
			<!--  -->
		</div>
	</button>
</main>

<style>
	.animate-rotateUp {
		animation-name: rotateUp;
		animation-duration: 3000ms;
		animation-timing-function: ease;
		animation-fill-mode: forwards;
	}
	@keyframes rotateUp {
		0% {
			transform: translateY(100%) rotate(var(--rotate-start));
			opacity: 0;
		}
		30% {
			opacity: 0;
		}
		100% {
			transform: translateY(0%) rotate(var(--rotate-end));
			opacity: var(--opacity-end);
		}
	}

	.animate-fadeIn {
		animation: fadeIn 500ms ease forwards;
	}
	@keyframes fadeIn {
		0% {
			opacity: 0;
		}
		100% {
			opacity: 1;
		}
	}

	.animate-fadeOut {
		animation: fadeOut 500ms ease forwards;
	}
	@keyframes fadeOut {
		0% {
			opacity: 1;
		}
		100% {
			opacity: 0;
		}
	}

	.animate-slideUp {
		animation: slideUp 500ms ease forwards;
	}
	@keyframes slideUp {
		0% {
			transform: translateY(50%);
		}
		100% {
			transform: translateY(0%);
		}
	}

	.animate-slideDown {
		animation: slideDown 500ms ease forwards;
	}
	@keyframes slideDown {
		0% {
			transform: translateY(0%);
		}
		100% {
			transform: translateY(50%);
		}
	}
</style>
