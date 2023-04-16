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
	<h3>襄助藝術</h3>
</Heading>
<Quote
	styling="ml-8 mt-[350px] w-[544px] text-[14px] font-[300] leading-[23px]"
	bind:animationStart
	bind:direction
>
	<blockquote>
		<p>
			{`「我從藝術家身上學到了嚴謹。」*嘉柏麗‧香奈兒既是藝術贊助人、靈感繆思，有時還是真正的藝術家，也為戲劇、芭蕾舞劇和電影設計服裝，她還熱愛閱讀，對巴洛克和拜占庭藝術以及斯拉夫文化充滿熱情，與眾多藝術家結下深厚友誼。她的閨蜜米西亞‧賽特（Misia Sert）引領她探索充滿蓬勃活力的藝術世界。她們一起與達基列夫（Diaghilev）、考克多（Cocteau）、史特拉汶斯基（Stravinsky）以及達利（Dali）為伴…… 嘉柏麗‧香奈兒為達基列夫的俄國芭蕾舞團提供資助，還為他的芭蕾舞劇《藍色列車》（Le Train bleu / The Blue Train）設計服裝。而考克多將香奈兒女士視為「當代最偉大的女性時裝設計師」，**香奈兒女士則為考克多的作品《安蒂岡妮》（Antigone）、《奧菲斯》（Orphée）和《俄狄浦斯王》（Œdipe Roi）設計服裝。香奈兒女士在自己的Bel Respiro 別墅款待史特拉汶斯基，並支持他的音樂創作。`}
			<br />
			{`嘉柏麗‧香奈兒曾於 1938 年將自己的 La Pausa 別墅借給薩爾瓦多‧達利 (Salvador Dali) 六個多月，讓他潛心作畫，為參加來年在美國紐約舉辦的畫展做準備。舞蹈家謝爾蓋‧里法爾（Serge Lifar）、傑克‧利普茲（Jacques Lipchitz）和畢卡索（Picasso）也是她的摯友。詩人皮耶‧雷維第（Pierre Reverdy）和馬克思‧雅克布（Max Jacob）也與她關係密切，而曾為她撰寫《香奈兒的孤傲與顛世》（The Allure of Chanel）一書的作家保羅•莫朗（Paul Morand），從她與卡培男孩之間的關係汲取靈感，創作了小說《Lewis et Irène》。尚‧考克多曾有這樣的說法：「她以近乎奇蹟的方式，遵循看似只適合畫家、音樂家和詩人的原則在時尚界應付自如。她有一種無形的影響力，賦予喧囂世俗一種無聲的尊貴。」嘉柏麗‧香奈兒，藝術家中的藝術家。`}
			<br />
			{`* 《香奈兒的孤傲與顛世》（The Allure of Chanel），作者：保羅•莫朗（Paul Morand），© 1976年，Hermannwww.editions-hermann.fr`}
			<br />
			{`**鳴謝尚‧考克多委員會（Jean Cocteau Committee）`}
		</p>
		<p class="mt-5">
			<span class="font-[600]"> {`嘉柏麗‧香奈兒和她的舞蹈家摯友謝爾蓋‧里法爾，攝於1937年`} </span>
			<br />
			{`Jean MORAL，1938年 © Brigitte Moral SAIF Paris`}
		</p>
	</blockquote>
</Quote>

<style>
</style>
