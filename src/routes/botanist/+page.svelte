<script lang="ts">
	import NavElement from './NavElement.svelte';

	const nav = ['FEATURE', ['SHAMPOO&TREATMENT -', 'OUR BATH -', 'BODY SOAP -'], 'PRODUCTS'];
</script>

<main class="absolute left-0 top-0 h-screen w-screen max-w-full">
	<nav
		class="fixed right-8 top-[40%] z-50 hidden flex-col items-end text-[14px] font-[500] leading-[1.2] tracking-[0.08rem] text-[#dd7994] md:flex"
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
	<button class="fixed bottom-5 right-0 z-50 md:hidden">
		<div class="h-16 w-12 rounded-l-full bg-[#520A4E] px-5 py-2">
			<!--  -->
		</div>
	</button>

	<div class="h-screen w-screen px-[12px] pb-[60px] pt-[30px] md:px-[110px] md:py-[80px]">
		<div class="relative h-full w-full">
			<div
				class="animate-slideUp absolute left-0 top-0 h-full w-full bg-[#DC94B8] [--opacity-end:0.2] [--rotate-end:-3deg] [transform-origin:center] [--rotate-start:-30deg]"
			/>
			<div
				class="animate-slideUp absolute left-0 top-0 h-full w-full bg-[#DC94B8] [--opacity-end:0.4] [--rotate-end:-6deg] [transform-origin:center] [--rotate-start:-30deg]"
			/>
			<div
				class="animate-slideUp relative h-full w-full bg-[url('botanist/img/kv_sp.jpg')] bg-cover bg-center [--opacity-end:1] [--rotate-end:0deg] [animation-delay:300ms] [--rotate-start:30deg] [transform-origin:left] md:bg-[url('botanist/img/kv.jpg')]"
			/>
		</div>
	</div>
	<!-- <img src="botanist/svg/logo-bk.svg" alt="" /> -->
</main>

<style>
	.animate-slideUp {
		/* animation: slideUp 3000ms ease var(--delay) forwards; */
		animation-name: slideUp;
		animation-duration: 3000ms;
		animation-timing-function: ease;
		animation-fill-mode: forwards;
	}
	@keyframes slideUp {
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
</style>
