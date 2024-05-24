<script lang="ts">
	import { onMount } from 'svelte';
	import Logo from './Logo.svelte';
	let prevY: number;
	let showNavbar = true;

	// $: console.log(showNavbar);
	// $: console.log(prevY);

	onMount(() => {
		prevY = window.scrollY;
	});
</script>

<svelte:window
	on:scroll={() => {
		let currY = window.scrollY;
		let deltaY = currY - prevY;

		if (deltaY > 0) {
			showNavbar = false;
			prevY = currY;
		} else if (deltaY < 0) {
			showNavbar = true;
			prevY = currY;
		}
	}}
/>

<div
	class="sticky top-0 z-50 flex h-fit w-full translate-y-[--position] transform-gpu flex-col items-center bg-white transition-transform"
	style:--position={showNavbar ? '0%' : '-100%'}
>
	<Logo />
</div>
<!-- <div class="flex h-[54px] w-full flex-row justify-center pt-3 text-[0.75rem] font-[600]">
	<div class="flex flex-row justify-center space-x-5">
		<span>高級訂製服</span>
		<span>服飾名品</span>
		<span>頂級珠寶</span>
		<span>腕錶</span>
		<span>眼鏡</span>
		<span>香氛</span>
		<span>彩妝</span>
		<span>保養</span>
	</div>
	<div class="ml-16">
		<span>關於</span>
	</div>
</div>
<div
	class="sticky top-[78px] flex h-[45px] w-full flex-row justify-center space-x-10 border-b-2 border-t-2 border-gray-100 bg-white pt-2 text-[12px] font-[600]"
>
	<a href="/the_founder">品牌創始人</a>
	<a href="/the_history">歷史</a>
	<a href="/the_stories">傳奇故事</a>
</div> -->
<slot></slot>
