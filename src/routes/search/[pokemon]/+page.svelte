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
    <img src={sprites[1]} alt={pokemon.response.name} />
    {/if}
  {/each}
</article>
<h1>{pokemon.response.name}</h1>
<section>
  <p><strong>Height:</strong> {pokemon.response.height}</p>
  <p><strong>Weight:</strong> {pokemon.response.weight}</p>
  <p><strong>Base Experience:</strong> {pokemon.response.base_experience}</p>
  <p><strong>Abilities:</strong> 
    {#each pokemon.response.abilities as ability}
      {ability.ability.name}{#if pokemon.response.abilities.indexOf(ability) < pokemon.response.abilities.length - 1}, {/if}
    {/each}
  </p>
  <p><strong>Types:</strong> 
    {#each pokemon.response.types as type}
      {type.type.name}{#if pokemon.response.types.indexOf(type) < pokemon.response.types.length - 1}, {/if}
    {/each}
  </p>
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
  }

  article img {
    max-width: 150px;
    height: auto;
  }

  h1 {
    text-transform: capitalize;
    color: #3b4cca;
    font-size: 2.5em;
    margin: 0.5em 0;
  }

  section {
    text-align: left;
    padding: 2em;
    max-width: 600px;
    margin: 0 auto;
  }

  section p {
    font-size: 1.1em;
    margin: 0.5em 0;
    color: #333;
  }

  section strong {
    color: #3b4cca;
  }

  :global(body) {
    overflow-y: auto;
  }
</style>
