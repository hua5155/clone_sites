<script lang="ts">
	import { writable } from 'svelte/store';

	const slides = [
		{
			image: '/Chanel/Slide/liberated.webp'
		},
		{
			image: '/Chanel/Slide/instinctive.webp'
		},
		{
			image: '/Chanel/Slide/visionary.webp'
		},
		{
			image: '/Chanel/Slide/free.webp'
		},
		{
			image: '/Chanel/Slide/patron.webp'
		},
		{
			image: '/Chanel/Slide/reader.webp'
		},
		{
			image: '/Chanel/Slide/pygmalion.webp'
		},
		{
			image: '/Chanel/Slide/lover_of_the_arts.webp'
		},
		{
			image: '/Chanel/Slide/avant_garde.webp'
		},
		{
			image: '/Chanel/Slide/luck.webp'
		}
	];
	let page = 0;
	const maxPage = 9;
	let direction = 'Right';
	$: imageAnimation = direction === 'Right' ? 'animate-moveLeft' : 'animate-moveRight';
	let animationStart = false;
	// $: if (animationStart === true) {
	// 	console.log('animation start'); // debug
	// } else {
	// 	console.log('animation end'); // debug
	// }
	const frontImage = writable({
		src: slides[0].image,
		height: 0
	});
	const backImage = writable({
		src: slides[1].image,
		height: 0
	});

	const handlePage = () => {
		if (animationStart === true) {
			return;
		}

		// console.log(`handlePage : ${direction}`); // debug

		if (direction === 'Left') {
			if (page === 0) {
				page = maxPage;
			} else {
				page -= 1;
			}
		}
		if (direction === 'Right') {
			if (page === maxPage) {
				page = 0;
			} else {
				page += 1;
			}
		}

		// $curImage = $nextImage;
		$backImage.src = slides[page].image;
		// console.log(`nextImage : ${$nextImage}`); // debug
		setTimeout(() => {
			animationStart = true;
		}, 200);
	};
</script>

<div class="h-fit w-full bg-zinc-800 py-10 text-white" style="transition: all 1000ms ease;">
	<h2 class="text-center text-[40px] font-[600]">關於 COCO 香奈兒</h2>

	<div class="mx-auto mt-20 flex w-[1600px] flex-row justify-between space-x-1">
		<!-- Left button -->
		<div class="w-[240px] bg-sky-500/50">
			<button
				class="mx-auto mt-[350px] w-full text-center"
				on:click={() => {
					direction = 'Left';
					handlePage();
				}}
			>
				Left
			</button>
		</div>

		<!-- <div class="relative w-full h-fit">
			<Slide1 />
			<div class="absolute left-0 top-0">
				<Slide1 />
			</div>
		</div> -->
		<div class="relative flex w-full flex-row">
			<div class="relative h-full w-[541px]">
				<!-- picture 1 -->
				<div
					class="absolute left-0 top-0 z-10 overflow-hidden
            {animationStart ? imageAnimation : ''}"
					style="width: 541px; height: {$frontImage.height}px;"
					on:animationstart={() => {
						console.log(`curImage : ${$frontImage.src}\nnextImage : ${$backImage.src}`);
					}}
					on:animationend={() => {
						$frontImage = $backImage;
						animationStart = false;
						// animationEnd = true;
					}}
				>
					<div
						class="absolute h-fit w-fit
              {direction === 'Left' ? ' right-0 top-0' : ''}"
						bind:clientHeight={$frontImage.height}
					>
						<img
							class="w-[541px] max-w-[541px] {animationStart ? 'animate-zoomIn' : ''}"
							src={$frontImage.src}
							alt=""
						/>
					</div>
				</div>
				<!-- picture 2 -->
				<div class="relative z-0 overflow-hidden" style="width: 541px;">
					<img
						class="w-[541px] max-w-[541px] {animationStart ? 'animate-zoomOut' : ''}"
						src={$backImage.src}
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

		<!-- Right button -->
		<div class="w-[240px] bg-sky-500/50">
			<button
				class="mx-auto mt-[350px] w-full text-center"
				on:click={() => {
					direction = 'Right';
					handlePage();
				}}
			>
				Right
			</button>
		</div>
	</div>
	<div class="mx-auto mt-16 w-fit">
		<span class="">{`${page + 1} / ${maxPage + 1}`}</span>
	</div>
</div>

<style>
	.animate-zoomIn {
		animation: zoomIn 2000ms ease;
	}
	@keyframes zoomIn {
		0% {
		}
		100% {
			transform: scale(1.5);
		}
	}

	.animate-zoomOut {
		animation: zoomOut 2000ms ease;
	}
	@keyframes zoomOut {
		0% {
			transform: scale(1.5);
		}
		100% {
			transform: scale(1);
		}
	}

	.animate-moveLeft {
		animation: moveLeft 2000ms ease;
	}
	@keyframes moveLeft {
		0% {
		}
		100% {
			width: 0px;
		}
	}

	.animate-moveRight {
		animation: moveRight 2000ms ease;
	}
	@keyframes moveRight {
		0% {
			/* width: 0px; */
		}
		100% {
			/* width: 541px; */

			left: 541px;
			width: 0px;
		}
	}

	.animate-slideLeft {
		animation: sildeLeft 2000ms ease;
	}
	@keyframes sildeLeft {
		0% {
			transform: translateX(541px);
		}
		100% {
			transform: translateX(-100%);
		}
	}

	.animate-slideRight {
		animation: sildeRight 2000ms ease;
	}
	@keyframes sildeRight {
		0% {
			transform: translateX(-100%);
		}
		100% {
			transform: translateX(541px);
		}
	}
</style>
