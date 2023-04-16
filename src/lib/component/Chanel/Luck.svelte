<script lang="ts">
	import Heading from './Heading.svelte';
	import Quote from './Quote.svelte';

	export let direction = '';
	export let animationStart = false;
</script>

<Heading
	styling="absolute left-[400px] top-[200px] z-30 text-[80px] font-[600]"
	bind:animationStart
	bind:direction
>
	<h3>幸運機遇</h3>
</Heading>
<Quote
	styling="ml-8 mt-[350px] w-[544px] text-[14px] font-[300] leading-[23px]"
	bind:animationStart
	bind:direction
>
	<blockquote>
		<p>
			{`在創作她的第一款香水作品 N°5 時，嘉柏麗‧香奈兒從不同的調香樣本中挑選了第 5 號樣本。在被問到「你要如何命名這款香水？」時，她回答：「我於一年中的第 5 個月 - 5 月 5 日推出由 5 款洋裝所組成的系列，我們就將編號 N°5 作為它的名稱吧，因為數字 5 會帶來好運。」*  機遇，也是尚‧考克多（Jean Cocteau）有一天在寫給她的便條上所探討的主題……她將麥穗視為機遇與幸運的象徵，在她位於康朋街的寓所中，金銀器工匠羅伯‧古森（Robert Goossens）為她製作的茶几底座上澆鑄了黃銅麥穗裝飾，畫家薩爾瓦多‧達利（Salvador Dali）也曾為她創作以麥穗為主題的畫作。`}
			<br />
			{`嘉柏麗‧香奈兒女士篤信冥冥中的安排…… 與其說她的命運由自己一手造就，不如說她在一生中極為注重各種預示和象徵符號的暗示。因此，她的生日——8月19日，成為另一款傳奇香水——N°19。而作為她星座標誌的獅子，也出現在她隨身攜帶的各種物品上，以莊重威嚴的姿態守護著她位於康朋街31號的公寓中……年幼時在奧巴辛修道院石板地上看到的星形鐫刻圖案，讓她一生追隨，並在她於1932年推出的「鑽石珠寶」（Bijoux de Diamants）系列中幻化為一件光芒璀璨的鑽石珠寶作品。`}
			<br />
			{`*Ernest BEAUX，《Souvenirs d’un parfumeur》（調香師的回憶），Industrie de la Parfumerie，卷1，N°7，1946年10月，第228至231頁`}
		</p>
		<p class="mt-5">
			<span class="font-[600]">
				{`嘉柏麗‧香奈兒的左手手印，以及她的簽名。`}
			</span>
			<br />
			{`© CHANEL`}
		</p>
	</blockquote>
</Quote>

<style>
</style>
