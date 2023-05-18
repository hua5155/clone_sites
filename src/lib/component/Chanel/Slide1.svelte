<script lang="ts">
	export let direction = '';
	export let zPosition = '';
	export let animationStart = false;
	$: imageAnimation = direction === 'Right' ? 'animate-moveLeft' : 'animate-moveRight';

	let imgHeight = 0;
</script>

<!-- Whole slide container -->
<div class="relative flex w-full flex-row">
	<!-- <div class="relative h-fit w-[541px]">
	</div> -->
	<div
		class="z-10 w-[541px] overflow-hidden
			{animationStart ? imageAnimation : ''}"
		style="height: {imgHeight}px;"
		on:animationend={() => {
			animationStart = false;
		}}
	>
		<div
			class="absolute h-fit w-fit {direction === 'left' ? 'right-0' : ''}"
			bind:clientHeight={imgHeight}
		>
			<img
				class="w-[541px] max-w-[541px] {animationStart ? 'animate-zoomIn' : ''}"
				src="/Chanel/Slide/1930_chanel_and_gigot.webp"
				alt=""
			/>
		</div>
	</div>

	<h3 class="absolute left-[400px] top-[200px] z-30 text-[80px] font-[600]">擺脫束縛</h3>
	<blockquote class="ml-8 mt-[350px] w-[544px] text-[14px] font-[300] leading-[23px]">
		<p>
			1930年時的香奈兒女士身穿長褲和橫紋水手衫，蓬鬆短髮迎風飛舞。其實，嘉柏麗‧香奈兒一向特立獨行。1920年，她在米西亞‧賽特（Misia
			Sert）的陪伴下前往威尼斯，在麗都（Lido）海灘上享受煦暖陽光的撫慰，對自己日曬後呈現的古銅膚色感到非常滿意。她熱衷於戶外生活，盡情探索各種體育運動和休閒娛樂活動，從高爾夫球、滑雪垂釣和出海遠航中品味獨到樂趣。
			<br />
			1906年，她在耶田‧巴爾森（Étienne Balsan）引導下對馬術產生了興趣，隨後又深受出色的馬球選手卡培男孩（Boy
			Capel）以及西敏公爵的影響。
			<br />
			這些戶外活動啟發她設計適合這些活動的服裝，雖然還未能稱為真正的運動服，但也已見雛型。「我為自己創作了運動服裝；不是因為其他女性需要參與運動，而是因為我自己要參與運動。我沒有外出是因為我需要設計時裝，而我設計時裝只因為我需要外出，因為我正在經歷這個世紀的生活。」*
			<br />
			*《香奈兒的孤傲與顛世》（The Allure of Chanel），作者：保羅•莫朗（Paul Morand），© 1976年，Hermann
			www.editions-hermann.fr
		</p>
		<p class="mt-5">
			<span class="font-[600]">
				嘉柏麗‧香奈兒和她的寵物狗 Gigot 在「La Pausa」別墅留影，攝於1930年
			</span>
			<br />
			© 版權所有
		</p>
	</blockquote>
</div>
