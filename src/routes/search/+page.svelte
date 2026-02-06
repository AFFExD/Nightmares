<script>
  let pokemon = null;
  let loading = false;
  let error = null;
  let searchTerm = '';

  async function handleSubmit(e) {
    e.preventDefault();
    const formData = new FormData(e.target);
    searchTerm = formData.get('search');
    
    if (!searchTerm) return;
    
    loading = true;
    error = null;
    pokemon = null;

    try {
      const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${searchTerm.toLowerCase()}`);
      
      if (!response.ok) {
        throw new Error(`${response.status}: ${response.statusText}`);
      }
      
      pokemon = await response.json();
    } catch (err) {
      error = err.message;
    } finally {
      loading = false;
    }
  }
</script>

<form onsubmit={handleSubmit}>
  <input type="text" name="search" placeholder="Sök upp en pokemon" />
</form>

{#if loading}
  <p>.. waiting</p>
{:else if error}
  <section class="error">
    <h1>You searched for: {searchTerm}</h1>
    <hr />
    <h2>{error}</h2>
  </section>
{:else if pokemon}
  <article>
    {#each Object.entries(pokemon.sprites) as sprites}
      {#if typeof sprites[1] == "string"}
        <img src={sprites[1]} alt={pokemon.name} />
      {/if}
    {/each}
  </article>
  <h1>{pokemon.name}</h1>
  <section>
    <p><strong>Height:</strong> {pokemon.height / 10} m</p>
    <p><strong>Weight:</strong> {pokemon.weight / 10} kg</p>
    <p><strong>Types:</strong> {pokemon.types.map(t => t.type.name).join(', ')}</p>
    <p><strong>Abilities:</strong> {pokemon.abilities.map(a => a.ability.name).join(', ')}</p>
  </section>
{/if}

<style>
  form {
    display: flex;
    gap: 10px;
    margin-bottom: 2em;
  }

  input {
    padding: 12px 16px;
    font-size: 16px;
    border: 2px solid #ddd;
    border-radius: 6px;
    width: 300px;
    transition: border-color 0.3s ease;
  }

  input:focus {
    outline: none;
    border-color: #4a90e2;
    box-shadow: 0 0 8px rgba(74, 144, 226, 0.3);
  }

  input::placeholder {
    color: #999;
  }

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

  .error {
    text-align: center;
  }
</style>
