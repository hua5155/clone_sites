<script lang="ts">
	export let id: number;
	export let date: string;
	export let heading: string;
</script>

<div class="box-shadow w-fit min-w-[500px] border-2 border-[#003e59] bg-white p-3">
	<div
		class="flex h-12 flex-row items-center justify-between border-2 border-[#003e59] font-sans text-[20px] font-[400] leading-[1.6rem] text-[#003e59]"
	>
		<div class="h-fit px-2 pb-1 align-middle">
			{`#${id}`}
		</div>
		<div class="h-fit px-2 pb-1 align-middle">
			{date}
		</div>
	</div>

	<div class="mt-3 border-2 border-[#003e59] bg-[#ffde05]">
		<h2 class="px-4 py-7 text-center text-[32px] text-[#003e59]">
			{heading}
		</h2>
	</div>

	<div class="mt-5">
		<h3 class="w-fit bg-[#003e59] px-2 text-white">GUEST</h3>
		<div class="border-b-2 border-t-2 border-[#003e59] px-5 py-8">
			<slot />
		</div>
	</div>

	<div class="flex justify-end text-[20px] font-[400] leading-[1.6rem] text-[#003e59]">
		<p class="w-fit">SHARE</p>
	</div>
</div>

<style>
	.box-shadow {
		filter: drop-shadow(-10px 10px 0px #003e59);
	}
</style>
