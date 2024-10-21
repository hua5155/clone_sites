<script lang="ts">
	import { fly } from 'svelte/transition';
	import { expoOut, expoIn } from 'svelte/easing';
	import Bloom from './Bloom.svelte';
	import NavElement from './NavElement.svelte';

	const nav = ['FEATURE', ['SHAMPOO & TREATMENT', 'OUR BATH', 'BODY SOAP'], 'PRODUCTS'];
	let navFlag = false;
</script>

<div class="absolute left-0 top-0 h-dvh w-dvw overflow-hidden">
	<div class="h-full w-full px-[12px] pb-[60px] pt-[30px] md:px-[110px] md:py-[80px]">
		<div class="relative h-full w-full">
			<div
				class="animate-rotate-up absolute left-0 top-0 h-full w-full bg-[#DC94B8]"
				style:--opacity-end="0.2"
				style:--rotate-start="-30deg"
				style:--rotate-end="-3deg"
				style="transform-origin: center;"
			></div>
			<div
				class="animate-rotate-up absolute left-0 top-0 h-full w-full bg-[#DC94B8]"
				style:--opacity-end="0.4"
				style:--rotate-start="-30deg"
				style:--rotate-end="-6deg"
				style="transform-origin: center;"
			></div>
			<div
				class="animate-rotate-up h-full w-full bg-[url('/botanist/img/kv_sp.jpg')] bg-cover bg-center md:bg-[url('/botanist/img/kv.jpg')]"
				style:--opacity-end="1"
				style:--rotate-start="30deg"
				style:--rotate-end="0deg"
				style="animation-delay: 300ms; transform-origin: left;"
			></div>
			<div
				class="absolute left-0 top-0 flex h-full w-full flex-col items-center justify-between px-[max(28px,_7.46667%)] py-[max(40px,_10.66667%)] md:items-start md:p-[60px]"
			>
				<img class="w-[70px] md:w-fit" src="/botanist/svg/logo-w.svg" alt="" />
				<Bloom />
			</div>
		</div>
	</div>

	<!-- Desktop nav bar -->
	<nav
		class="fixed right-8 top-[40%] hidden flex-col items-end text-[14px] font-[500] leading-[23px] tracking-[0.08rem] text-[#dd7994] md:flex"
	>
		<ul class="flex flex-col items-end">
			{#each nav as url}
				<NavElement {url} />
			{/each}
		</ul>
		<div class="pt-7"></div>
		<button
			class="group flex h-[50px] w-fit items-center justify-center rounded-full bg-[#dd7994] px-5 font-[700] leading-[1] text-white transition-colors duration-300 hover:bg-[#520A4E]"
		>
			<div class="flex h-[14px] w-fit flex-col overflow-hidden">
				<span
					class="-translate-y-0 transition-transform duration-300 after:block after:content-['CAMPAIGN'] group-hover:-translate-y-1/2"
				>
					CAMPAIGN
				</span>
			</div>
		</button>
	</nav>

	<!-- Mobile nav bar -->
	{#if navFlag === true}
		<div
			class="absolute left-0 top-0 h-full w-full bg-[url('/botanist/img/bg.jpg')] bg-cover bg-right-top px-[13%] py-[70px] md:hidden"
			in:fly={{ duration: 800, y: '100%', easing: expoOut }}
			out:fly={{ duration: 500, y: '100%', easing: expoIn }}
		>
			<div>
				<div class="flex h-fit w-full justify-center">
					<img src="/botanist/svg/logo-bk.svg" alt="" />
				</div>
				<div class="pt-16"></div>
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
		class="fixed bottom-5 right-0 h-16 w-12 rounded-l-full bg-[#520A4E] md:hidden"
		on:click={() => {
			navFlag = !navFlag;
		}}
	>
	</button>
</div>

<style>
	.animate-rotate-up {
		animation-name: rotateUp;
		animation-duration: 3000ms;
		animation-timing-function: ease;
		animation-fill-mode: forwards;
	}
	@keyframes rotateUp {
		0% {
			transform: translate3d(0, 100%, 0) rotate(var(--rotate-start));
			opacity: 0;
		}
		30% {
			opacity: 0;
		}
		100% {
			transform: translate3d(0, 0%, 0) rotate(var(--rotate-end));
			opacity: var(--opacity-end);
		}
	}
</style>
