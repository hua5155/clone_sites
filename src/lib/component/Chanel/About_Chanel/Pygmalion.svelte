<script lang="ts">
	import FrontSlide from './FrontSlide.svelte';
	import BackSlide from './BackSlide.svelte';

	export let position = '';
</script>

<svelte:component
	this={position.toLowerCase() === 'front' ? FrontSlide : BackSlide}
	imgSrc="/Chanel/Slide/pygmalion.webp"
	headingPos="absolute left-[240px] top-[200px]"
>
	<h3 class="text-[80px] font-[600]" slot="heading">獨具慧眼的藝術家</h3>
	<blockquote class="ml-8 mt-[350px] w-[544px] text-[14px] font-[300] leading-[23px]" slot="quote">
		<p>
			{`香奈兒女士擅於發掘人才。她為此聯繫好友，及時動用人脈……1936年，她向導演尚‧雷諾瓦（Jean Renoir）推薦了年輕的盧契諾‧維斯康堤（Luchino Visconti），尚‧雷諾瓦立即發現了這位對電影充滿熱誠的義大利年輕人才，並聘請其為導演助理。`}
			<br />
			{`數年後，維斯康堤將法蘭高‧齊費里尼（Franco Zeffirelli）派往巴黎，並請嘉柏麗‧香奈兒將法蘭高‧齊費里尼介紹給法國電影界。香奈兒女士將他引薦給碧姬‧芭杜（Brigitte Bardot）和羅傑‧瓦迪姆（Roger Vadim），也從此開啟了這位義大利導演的銀幕生涯。`}
		</p>
		<p class="mt-5">
			<span class="font-[600]"> {`女演員珍妮‧摩露和嘉柏麗‧香奈兒，1960年攝於好萊塢`} </span>
			<br />
			{`© Giancarlo BOTTI/GAMMA RAPHO`}
		</p>
	</blockquote>
</svelte:component>

<style>
</style>
