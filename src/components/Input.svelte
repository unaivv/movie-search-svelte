<script>
    import Movie from "./Movie.svelte";
 
    let value = "";
    let response = [];
    const handleInput = (e) => (value = e.target.value);

    $: if (value.length > 2) {
        console.log(`https://www.omdbapi.com/?s=${value}&apikey=422350ff`)
        response = fetch(`https://www.omdbapi.com/?s=${value}&apikey=422350ff`)
            //.then(res => !res.ok() && new Error('Something bad happened with the fetching movies'))
            .then((res) => res.json())
            .then(apiResponse => apiResponse.Search || []);
    }
</script>

<input {value} placeholder="Search movies..." on:input={handleInput} />

{#await response}
    <p><strong>Loading...</strong></p>
{:then movies}
    {#each movies as { Title, Poster, Year }, index}
        <Movie title={Title} poster={Poster} year={Year} />
    {:else}
        <p><strong>No hay resultados</strong></p>
    {/each}
{:catch error }
    <p>❌  There has been an error: {error}</p>
{/await}