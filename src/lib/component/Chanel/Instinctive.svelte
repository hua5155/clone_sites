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
	<h3>天性使然</h3>
</Heading>
<Quote
	styling="ml-8 mt-[350px] w-[544px] text-[14px] font-[300] leading-[23px]"
	bind:animationStart
	bind:direction
>
	<blockquote>
		<p>
			{`香奈兒女士於 1910年開設了自己的第一間帽子精品店，讓整個巴黎趨之若鶩，為建立香奈兒時尚王國奠定第一塊基石。兩年後，她敏銳地覺察到濱海度假小鎮的蓬勃發展，於是選擇在杜維埃（Deauville）開設了自己的第二間精品店。`}
			<br />
			{`隨後，她於1915 年在迅速崛起的時尚度假勝地比亞里茨（Biarritz）開設了自己的高級訂製服精品店。嘉柏麗‧香奈兒從
			1918 年起遷入康朋街 31 號。她於 1921 年推出 N°5 香水，是第一款以獨特香調和簡約大方的瓶身造型顛覆當時調香陳規的時裝設計師香水。1937年，她親自為自己宣傳，在廣告中亮相，可說是又一大膽創新之舉……1932 年推出的「鑽石珠寶」（Bijoux de Diamants）系列轟動一時，讓沉寂的珠寶界為之驚嘆，由此意識到香奈兒女士再次打破陳規。她是令人敬畏的女商人，也是第一位創辦跨國企業的獨立自主女性，她從未被自己的敏銳直覺所蒙蔽。`}
		</p>
		<p class="mt-5">
			<span class="font-[600]"> {`工作中的香奈兒女士，攝於1937年`} </span>
			<br />
			{`© 攝影：Roger Schall / Schall Collection`}
		</p>
	</blockquote>
</Quote>

<style>
</style>
