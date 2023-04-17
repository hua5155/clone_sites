<script lang="ts">
	import FrontSlide from './FrontSlide.svelte';
	import BackSlide from './BackSlide.svelte';

	export let position = '';
	// let component = BackSlide
	// $: component = position.toLowerCase() === 'front' ? FrontSlide : BackSlide
</script>

<svelte:component
	this={position.toLowerCase() === 'front' ? FrontSlide : BackSlide}
	imgSrc="/Chanel/Slide/free.webp"
	headingPos="absolute left-[400px] top-[200px]"
>
	<h3 class="text-[80px] font-[600]" slot="heading">自由自在</h3>
	<blockquote class="ml-8 mt-[350px] w-[544px] text-[14px] font-[300] leading-[23px]" slot="quote">
		<p>
			{`嘉柏麗‧香奈兒曾調侃自己：「我是奧維涅（Auvergne）唯一一座活火山。」永遠不要被任何人束縛，尤其是被男性束縛，是這位性格如火的設計師的出眾特點。然而，她亦是用情至深之人，這也是她自身的矛盾之處。嘉柏麗‧香奈兒一生追求獨立自主，但在面對愛情時則全心投入。`}
			<br />
			{`她在創業之時獲得卡培男孩（Boy Capel）的資助，在其協助下於 1910 年在巴黎開設帽子精品店，並於 1912年於杜維埃開設精品店。而令嘉柏麗‧香奈兒引以為傲的是，她之後將這份資助悉數償還。這既是原則問題，也近乎一種生存本能：不要，也從不依靠任何人，不惜一切代價追求自在無拘。同樣是出於對自由的考慮，她購置巴黎近郊加爾舍（Garches）的Bel Respiro 別墅，並在法國蔚藍海岸（Riviera）的洛克布魯馬丁岬建造了 La Pausa別墅。當然，還有她在巴黎康朋街 31 號的寓所。自由無束，獨立自主，是她為女性樹立的完美典範。`}
			<br />
			{`*《香奈兒的孤傲與顛世》（The Allure of Chanel），作者：保羅•莫朗（Paul Morand），© 1976年，Hermann
		www.editions-hermann.fr`}
		</p>
		<p class="mt-5">
			<span class="font-[600]"> {`在「La Pausa」別墅中的嘉柏麗‧香奈兒，攝於1938年`} </span>
			<br />
			{`© 攝影：Roger Schall - Schall Collection`}
		</p>
	</blockquote>
</svelte:component>

<style>
</style>
