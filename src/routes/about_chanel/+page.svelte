<script lang="ts">
	import Logo from './Logo.svelte';
	import Signature from './Signature.svelte';
	import Slide from './Slide.svelte';
	import Art from './Art.svelte';
	import Video from './Video.svelte';
</script>

<main class=" h-screen w-screen">
	<div class="sticky top-0 flex h-fit w-full flex-col items-center bg-white">
		<Logo />
	</div>
	<div class="flex h-[54px] w-full flex-row justify-center pt-3 text-[0.75rem] font-[600]">
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
	</div>
	<h1 class="w-full text-center text-[50px] font-[600]">品牌創始人</h1>
	<div class="flex h-[2574px] w-full justify-center">
		<Signature />
	</div>
	<div class="mx-auto flex w-[590px] flex-col items-center">
		<span class="text-[30px] font-[600]">「願我的傳奇淵遠流長，恆久愉悅！」*</span>
		<span class="text-center text-[14px] font-[300] italic">
			{`* 《香奈兒的孤傲與顛世》（The Allure of Chanel），作者：保羅•莫朗（Paul Morand），© 1976年，Hermann www.editions-hermann.fr`}
		</span>
		<span class="text-[14px] font-[300]">© Man Ray Trust / ADAGP，巴黎，2016年</span>
	</div>
	<div class="mx-auto w-[590px] text-center text-[14px] font-[300]">
		<span class="">
			{`嘉柏麗‧香奈兒以自己選擇的方式生活，從歷經艱辛的年幼孤女到晉身為事業成功的女商人，造就出她與眾不同、大膽率真的個性，讓她遠遠領先所處的時代。她擁有忠誠真摯的友誼，享受著親密熾熱的愛戀，她對文化、探索和旅行有著無法抑制的渴望，這一切，都對她的性格帶來重要影響。她讓女性的穿著擺脫束縛，化繁為簡，並將男裝特色融入女裝設計，呈現出具有遠見的魅力風格，體現洋溢現代氣息的永恆經典。她以從容大方的姿態配戴珍珠和鑽石，搭配經典香水彰顯個人風格。她是個前衛女性，是一位以自己的生活方式與多重面貌為她一手創辦的品牌樹立價值理念的先鋒人物。同時，持續不斷為女性帶來啟發與靈感。`}
		</span>
	</div>
	<Slide />
	<Art />
	<Video />
</main>

<style></style>
