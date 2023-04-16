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
	<h3>熱愛閱讀</h3>
</Heading>
<Quote
	styling="ml-8 mt-[350px] w-[544px] text-[14px] font-[300] leading-[23px]"
	bind:animationStart
	bind:direction
>
	<blockquote>
		<p>
			{`「書籍一直是我最好的朋友。」* 嘉柏麗‧香奈兒有一天向保羅‧莫朗說。從在奧巴辛（Aubazine）修道院閱讀聖詩開始，書籍與嘉柏麗‧香奈兒相伴一生。在她位於康朋街的寓所中，各種書籍沉重地堆疊於牆面架上。其中一本打開著，旁邊還擺放著一副眼鏡……躺在米色麂皮沙發上，靠著菱格紋抱枕，嘉柏麗‧香奈兒飽覽群書。`}
			<br />
			{`既有索福克勒斯（Sophocles）、荷馬（Homer）、普魯塔克（Plutarch）和維吉爾（Virgil）的著作，也有拉伯雷（Rabelais）、但丁（Dante）、莎士比亞（Shakespeare）和蒙田（Montaigne）的作品。拉布魯耶（La Bruyère）、莫里哀（Molière）、塞凡提斯（Cervantes）的作品與盧梭（Rousseau）、伏爾泰（Voltaire）、帕斯卡（Pascal）的作品並排擺放。當中也不乏普魯斯特（Proust）、勃朗特（Brontë）、史坦（Stein）、杜斯妥也夫斯基（Dostoevsky）和托爾斯泰（Tolstoy）。此外還有詩人里爾克（Rilke）、波特萊爾（Baudelaire）、阿波利奈爾（Apollinaire）、魏爾倫（Verlaine）、考克多（Cocteau）、馬克思‧雅克布（Max Jacob）和雷維第（Reverdy）的詩篇。`}
			<br />
			{`*《香奈兒的孤傲與顛世》（The Allure of Chanel），作者：保羅•莫朗（Paul Morand），© 1976年，Hermann www.editions-hermann.fr`}
		</p>
		<p class="mt-5">
			<span class="font-[600]"> {`在巴黎康朋街 31 號寓所中的嘉柏麗‧香奈兒，攝於1937年`} </span>
			<br />
			{`攝影：Jean Moral ©  Brigitte Moral`}
		</p>
	</blockquote>
</Quote>

<style>
</style>
