<script>
    export let title, poster, year
</script>

<article>
    <img src={poster} alt={title} />
    <h3>
        {title}
        {#if 2020 - year < 5}
            <small>🆕</small>
        {/if}
        <small class="year">{year}</small>
    </h3>
</article>

<style>
    article{
        border: 1px solid #eee;
        border-radius: 4px;
        margin-bottom: 8px;
        padding: 16px;
    }
    .year{
        font-weight: normal;
    }
</style>