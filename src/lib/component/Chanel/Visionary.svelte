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
	<h3>高瞻遠矚</h3>
</Heading>
<Quote
	styling="ml-8 mt-[350px] w-[544px] text-[14px] font-[300] leading-[23px]"
	bind:animationStart
	bind:direction
>
	<blockquote>
		<p>
			{`針織服裝、水手衫、斜紋軟呢套裝和外套、兩件式針織衫、小黑洋裝、雙色鞋、皮革鍊帶菱格紋肩背包款、珍珠項鍊……嘉柏麗‧香奈兒創造出全新魅力姿態，打造當代女性穿著的永恆典範風格語彙。`}
			<br />
			{`她心目中的女性時裝樣貌簡約大方，線條低調優雅，完全不會束縛女性的一舉一動，讓她們得以輕鬆自如地面對日常生活，隨之而來的，還有其他創新之舉。`}
			<br />
			{`她是首位於1921年推出香水的服裝設計師，憑藉敏銳觸覺征服世界，為此，她說：「香水，是奢侈品。」*而對於高級珠寶，她也竭力化繁為簡，摒棄死板的寶石鑲座，甚至設計出可配戴於頭上的珠寶髮飾。讓珍貴的珠寶能趨近日常生活，在當時也是一種令人驚嘆的現代眼光。嘉柏麗‧香奈兒也採取創新的方式與女性溝通交流，她之所以於1931年同意前往美國好萊塢工作，並為美國女演員設計服裝，是因為她明白，正如她對自己所說：「如今的時尚可以透過電影來實現。」**`}
			<br />
			{`*在Guy Job拍攝的節目《DIM DAM DOM》中對賈克‧夏佐（Jacques Chazot）訪問的回答，1969 年`}
			<br />
			{`**《電影雜誌》（La Revue du Cinéma），1931年9月1日`}
		</p>
		<p class="mt-5">
			<span class="font-[600]">
				{`嘉柏麗‧香奈兒女士在她位於洛克布魯（Roquebrune）的「La Pausa」別墅花園中，攝於1938年`}
			</span>
			<br />
			{`© 攝影：Roger Schall - Schall Collection`}
		</p>
	</blockquote>
</Quote>

<style>
</style>
