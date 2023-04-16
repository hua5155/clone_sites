<script lang="ts">
	let frontImgWidth = 541;
	let frontImgHeight = 0;
	let backImgWidth = 541;
	let backImgHeight = 0;
	let direction = '';
	let frontAnimation = '';
	let backAnimation = '';
	let frontAnimationStart = false;
	let backAnimationStart = false;
</script>

<main class="h-fit w-screen bg-black">
	<!-- Div width control -->
	<div class="mx-auto w-fit py-10">
		<input class="h-10 w-40 rounded-lg bg-gray-500 px-5" type="number" bind:value={frontImgWidth} />
		<input class="h-10 w-40 rounded-lg bg-gray-500 px-5" type="number" bind:value={backImgWidth} />

		<button
			class="h-10 w-fit rounded-lg bg-cyan-500 px-5"
			on:click={() => {
				frontImgWidth = 541;
			}}
		>
			Reset width
		</button>

		<button
			class="h-10 w-fit rounded-lg bg-cyan-500 px-5"
			on:click={() => {
				frontAnimationStart = false;
				backAnimationStart = false;
			}}
		>
			Reset animation flag
		</button>

		<button
			class="h-10 w-fit rounded-lg bg-cyan-500 px-5"
			on:click={() => {
				direction = 'left';
				frontAnimation = 'animate-shrinkRight';
				backAnimation = 'animate-appearLeft';
				frontAnimationStart = true;
				backAnimationStart = true;
			}}
		>
			Left
		</button>

		<button
			class="h-10 w-fit rounded-lg bg-cyan-500 px-5"
			on:click={() => {
				direction = 'right';
				frontAnimation = 'animate-shrinkLeft';
				backAnimation = 'animate-appearRight';
				frontAnimationStart = true;
				backAnimationStart = true;
			}}
		>
			Right
		</button>
	</div>

	<!-- Wrapper for two images -->
	<div class="relative mx-auto h-fit py-5">
		<!-- Container using for overflow -->
		<div
			class="absolute left-0 z-10 overflow-hidden {frontAnimationStart ? frontAnimation : ''}"
			style="
        width: {frontImgWidth}px;
        height: {frontImgHeight}px;
			"
			on:animationend={() => {
				// frontAnimationStart = false;
			}}
		>
			<!-- Wrapper div to get img dimension? -->
			<div
				class="absolute h-fit w-fit {direction === 'left' ? 'right-0' : ''}"
				bind:clientHeight={frontImgHeight}
			>
				<img
					class="w-[541px] max-w-[541px]"
					src="/Chanel/Slide/1930_chanel_and_gigot.webp"
					alt=""
				/>
			</div>
		</div>

		<!-- picture 2 -->
		<div
			class="relative z-0 overflow-hidden {backAnimationStart ? backAnimation : ''}"
			style="
				width: 0px;
				height: {backImgHeight}px;
			"
			on:animationend={() => {
				// backAnimationStart = false;
			}}
		>
			<!-- Wrapper div to get img dimension? -->
			<div
				class="absolute h-fit w-fit {direction === 'right' ? 'right-0' : ''}"
				bind:clientHeight={backImgHeight}
			>
				<img class="w-[541px] max-w-[541px]" src="/Chanel/Slide/1937_chanel_working.webp" alt="" />
			</div>
		</div>
	</div>
</main>

<style>
	.animate-shrinkLeft {
		animation: shrinkLeft 2000ms ease normal forwards;
	}
	@keyframes shrinkLeft {
		0% {
			width: 541px;
		}
		100% {
			width: 0px;
		}
	}

	.animate-shrinkRight {
		animation: shrinkRight 2000ms ease normal forwards;
	}
	@keyframes shrinkRight {
		0% {
			width: 541px;
			margin-left: 0px;
		}
		100% {
			width: 0px;
			margin-left: 541px;
		}
	}

	.animate-appearLeft {
		animation: appearLeft 2000ms ease 200ms normal forwards;
	}
	@keyframes appearLeft {
		0% {
			width: 0px;
		}
		100% {
			width: 541px;
		}
	}

	.animate-appearRight {
		animation: appearRight 2000ms ease 200ms normal forwards;
	}
	@keyframes appearRight {
		0% {
			width: 0px;
			margin-left: 541px;
		}
		100% {
			width: 541px;
			margin-left: 0px;
		}
	}
</style>
