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
	<h3>前衛時尚</h3>
</Heading>
<Quote
	styling="ml-8 mt-[450px] w-[544px] text-[14px] font-[300] leading-[23px]"
	bind:animationStart
	bind:direction
>
	<blockquote>
		<p>
			{`打破陳規和性別界限，開創未來經典時尚，彰顯剛柔並濟的魅力，嘉柏麗‧香奈兒勇於嘗試一切：將男裝常見的斜紋軟呢布料運用於女裝設計，讓原本看似廉價的針織布料備受青睞，設計出沙灘裝和寬鬆連身洋裝。`}
			<br />
			{`她心意已決，無所畏懼：「其他顏色都不適宜。而我，要用黑色妝扮女性。」無論是她的設計風格、時裝作品乃至她的個性中，皆流露出一種桀驁不馴的反叛精神。她留著短髮，在陽光下將肌膚曬成小麥色，從賽馬場上的男士外套汲取靈感，將菱格紋圖案運用在她的經典包款設計上。她熱衷於滑雪垂釣、高爾夫球，甚至長時間策馬疾馳。她獨立自主的態度和追求自由的精神，讓她不會因為引發爭議而感到膽怯，也不會因為驚世駭俗的愛情而卻步。一直努力工作，為爭取自主決定命運，乃至執掌公司而抗爭。在1931年6月發表的《我們提名名人堂》（We nominate for the Hall of Fame）一文中，《Vanity Fair》雜誌對她作出以下評論：「嘉柏麗‧香奈兒是將現代原則運用到時裝中的第一人，圍繞她身邊的好友，皆為法國最具影響力的名人，而她將敏銳的商業理念與雍容大器的個性，以及對藝術的幻想與真切的樂觀精神相結合。」一直引領時代。`}
			<br />
			{`*《香奈兒的孤傲與顛世》（The Allure of Chanel），作者：保羅•莫朗（Paul Morand），© 1976年，Hermann www.editions-hermann.fr`}
		</p>
		<p class="mt-5">
			<span class="font-[600]">
				{`在「La Pausa」別墅花園中的嘉柏麗‧香奈兒女士，攝於1938年`}
			</span>
			<br />
			{`© 攝影：Roger Schall - Schall Collection`}
		</p>
	</blockquote>
</Quote>

<style>
</style>
