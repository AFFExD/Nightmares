<script>
  /** @type {import('./$types').PageData} */
  export let data;
</script>

{#await data}
  <p>.. waiting</p>
{:then pokemon} 
<article>
  {#each Object.entries(pokemon.response.sprites) as sprites}
    {#if typeof sprites[1] == "string"}
    <img src={sprites[1]} />
    {/if}
  {/each}
</article>
<h1>{pokemon.response.name}</h1>
<section>
  <p><strong>Height:</strong> {pokemon.response.height / 10} m</p>
  <p><strong>Weight:</strong> {pokemon.response.weight / 10} kg</p>
  <p><strong>Types:</strong> {pokemon.response.types.map(t => t.type.name).join(', ')}</p>
  <p><strong>Abilities:</strong> {pokemon.response.abilities.map(a => a.ability.name).join(', ')}</p>
</section>

{/await}

<style>
  article {
    display: flex;
    width: 90%;
    height: 30%;
    gap: 1em;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
  }

  img {
    max-width: 150px;
    max-height: 150px;
    object-fit: contain;
  }

  section {
    width: 90%;
    margin-top: 2em;
  }

  p {
    font-size: 18px;
    margin: 10px 0;
  }
</style>
