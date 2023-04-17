<script lang="ts">
	import FrontSlide from './FrontSlide.svelte';
	import BackSlide from './BackSlide.svelte';

	export let position = '';
</script>

<svelte:component
	this={position.toLowerCase() === 'front' ? FrontSlide : BackSlide}
	imgSrc="/Chanel/Slide/lover_of_the_arts.webp"
	headingPos="absolute left-[400px] top-[200px]"
>
	<h3 class="text-[80px] font-[600]" slot="heading">熱愛藝術</h3>
	<blockquote class="ml-8 mt-[510px] w-[544px] text-[14px] font-[300] leading-[23px]" slot="quote">
		<p>
			{`學習、探索藝術，從藝術汲取靈感，培養自己的巧思創意，這是嘉柏麗‧香奈兒一生奉行的信念。嘉柏麗‧香奈兒對繪畫、雕塑、建築和歷史深感興趣，在與狄米崔大公爵墮入愛河之後，鐘情於斯拉夫文化所散發的迷人魅力。自此，俄式上衣、大衣、彩色凸圓形寶石和拜占庭十字架如繁花綻放，點綴她的系列作品。`}
			<br />
			{`她在好友米西亞（Misia）和荷西‧瑪利亞‧賽特（José Maria Sert）夫婦陪同下遊覽了羅馬和威尼斯，為裝飾精美的教堂、宏偉華麗的巴洛克藝術所傾倒。  在她的風格詞彙中，質樸的古典風格與金光璀璨的華麗裝飾自然融合。嘉柏麗‧香奈兒在寓所中擺放了許多中國烏木漆面屏風，數量多達三十多件，實屬珍罕！而這些屏風也為她帶來無限靈感。她在佈置自己的別墅和公寓時以不拘一格的方式將各種風格與時代氣息完美結合，一切皆「奢華有序」，為她帶來取之不盡的創意靈感：晶瑩剔透的水晶球、光芒閃耀的吊飾、華貴的鏡面、沉寂的色彩以及各種青銅器，在這裡，東方與西方融貫匯集，也對香奈兒風格產生重要影響。`}
		</p>
		<p class="mt-5">
			<span class="font-[600]">
				{`站在中國烏木漆面屏風前的嘉柏麗‧香奈兒，1937年攝於巴黎康朋街31號`}
			</span>
			<br />
			{`© Boris Lipnitzki / Roger-Viollet`}
		</p>
	</blockquote>
</svelte:component>

<style>
</style>
