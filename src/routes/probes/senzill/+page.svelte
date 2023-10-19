<script lang="ts">
	// @ts-nocheck
	import SelectionButtons from "$lib/selection-buttons.svelte"
	import "../../../styles.css"
	export const ssr = false
	let canPass = false
	let currentQuestion = 0
	const correctOptions = ["desarollar", "Al Xavi le gusta la programación"]

	function wrong(e: any) {
		canPass = true
		e.target.style.backgroundColor = "rgb(248, 113, 113)"
	}
	function correct(e: any) {
		canPass = true
		e.target.style.backgroundColor = "rgb(74, 222, 128)"
	}
	function pass() {
		canPass = false
		currentQuestion++
	}
</script>

<svelte:head>
	<title>Comencem! | Català Per Devs</title>
</svelte:head>

<main
	class="w-full h-[100vh] max-w-[750px] p-[20px] m-auto flex justify-center items-center flex-col"
>
	{#if currentQuestion === 0}
		<article class="w-full h-full flex justify-center items-center flex-col">
			<section class="w-full py-[20px]">
				<h1 class="text-[25px] font-bold text-start py-[20px]">
					¿Què vol dir desenvolupar?
				</h1>
			</section>
			<section class="flex flex-col gap-[20px] w-full">
				<SelectionButtons click={(e) => wrong(e)}>ordenar</SelectionButtons>
				<SelectionButtons click={(e) => wrong(e)}>programar</SelectionButtons>
				<SelectionButtons click={(e) => wrong(e)}>desordenar</SelectionButtons>
				<SelectionButtons click={(e) => correct(e)}>desarollar</SelectionButtons>
			</section>
			{#if canPass}
				<section class="w-full text-start py-[20px]">
					<button
						class="text-start py-[12px] px-[20px] bg-slate-300 rounded-[7px]"
						on:click={() => pass()}
					>
						Continuar &rarr;
					</button>
					<p class="mt-[10px]">
						Solució: {correctOptions[currentQuestion]}
					</p>
				</section>
			{/if}
		</article>
	{:else if currentQuestion === 1}
		<article class="w-full h-full flex justify-center items-center flex-col">
			<section class="w-full py-[20px]">
				<h1 class="text-[25px] font-bold text-start py-[20px]">
					Què vol dir "En Xavi li agrada la programació"
				</h1>
			</section>
			<section class="flex flex-col gap-[20px] w-full">
				<section class="flex flex-col gap-[20px] w-full">
					<SelectionButtons click={(e) => wrong(e)}
						>Al Xavi le gusta ordenar</SelectionButtons
					>
					<SelectionButtons click={(e) => wrong(e)}
						>Al Xavi le gusta desarollar</SelectionButtons
					>
					<SelectionButtons click={(e) => correct(e)}
						>Al Xavi le gusta la programación</SelectionButtons
					>
					<SelectionButtons click={(e) => wrong(e)}
						>Al Xavi le gusta subir escaleras</SelectionButtons
					>
				</section>
			</section>
			{#if canPass}
				<section class="w-full text-start py-[20px]">
					<button
						class="text-start py-[12px] px-[20px] bg-slate-300 rounded-[7px]"
						on:click={() => pass()}
					>
						Continuar &rarr;
					</button>
					<p class="mt-[10px]">
						Solució: {correctOptions[currentQuestion]}
					</p>
				</section>
			{/if}
		</article>
	{/if}
</main>
