<script lang="ts">
	export let id: number;
	export let date: string;
	export let heading: string;
	export let name: string;
</script>

<div
	class="w-[300px] border-2 border-[#003e59] bg-white p-3 drop-shadow-[-3px_3px_0px_#003e59] xl:w-[500px]"
>
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

	<div class="pt-3"></div>
	<div class="border-2 border-[#003e59] bg-[#ffde05]">
		<h2 class="px-4 py-7 text-center text-[32px] text-[#003e59]">
			{heading}
		</h2>
	</div>

	<div class="pt-5"></div>
	<h3 class="w-fit bg-[#003e59] px-2 text-white">GUEST</h3>
	<div class="border-b-2 border-t-2 border-[#003e59] px-5 py-8">
		<div class="flex flex-row space-x-2">
			<div class="h-[110px] w-[110px] border-2 border-[#003e59] bg-pink-400" />
			<p
				class="h-fit w-fit bg-[#ffde05] text-[20px] font-[400] capitalize leading-[1.6rem] text-[#003e59]"
			>
				{name}
			</p>
		</div>
	</div>

	<div class="flex justify-end text-[20px] font-[400] leading-[1.6rem] text-[#003e59]">
		<p class="w-fit">SHARE</p>
	</div>
</div>
