<script>
import { space } from "svelte/internal"

    export let initialCounter = 0
    export let maxCounter = 9

	let contador = initialCounter

	const handleClick = () => {
		contador++
	}

    $: isEvenOrOdd = contador % 2 === 0 ? 'Is Even' : 'Is Odd'
    $: if(contador > maxCounter){
        contador = maxCounter
    }

</script>

<div>
	<button on:click={handleClick}>Incrementar</button>
    <span>{contador}</span>
    <span>{isEvenOrOdd}</span>
</div>

<style>
	span {
        color: red;
    }
</style>