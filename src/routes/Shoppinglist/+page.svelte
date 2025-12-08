<script>
    let newvara = "";
    
    let varor = $state([
    { name: "banana", bought: false }, 
    { name: "apple", bought: false }
]);

function addVara() {
    const name = newvara.trim();
    if (!name) return; // Stoppa om namnet är tomt
    
    varor.push({ name, bought: false });
    newvara = ""; // Nollställ input
}
function toggleBought(index) {
    varor[index].bought = !varor[index].bought;
}
</script>

<main class="container">

    <h1>Shopping List</h1>
    <div class="add-row">
    <input 
        type="text"
        bind:value={newvara}
        placeholder="Skriv in vara..."
    />
    <button type="button" onclick={addVara} >Lägg till</button>
</div>
    


    <div class="categories_container">
        <section>
        <h2>Shopping catalog</h2>
        <ol>
    {#each varor as vara, i}
        {#if !vara.bought}
            <li>
                {vara.name}
                <button onclick={() => toggleBought(i)}>Add to cart</button>
            </li>
        {/if}
    {/each}
        </ol>
        </section>
        <section>
        <h2>Shopping cart</h2>
        <ol>
    {#each varor as vara, i}
        {#if vara.bought}
            <li>
                {vara.name}
                <button onclick={() => toggleBought(i)}>Remove</button>
            </li>
        {/if}
    {/each}
        </ol>
        </section>

        <!-- Kategorier för shoppinglistan går här -->
     </div>
</main>    
    <style>

.container{
    background-color: #f0f0f0;
    display: grid;
    justify-content: center;
    align-items: center;
    width: 60vw;
    height: 70vh;
    border-radius: 20px;
    grid-template-rows: 1fr 8fr 1fr;
    grid-template-columns: 1fr;
}
        
.categories_container{
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    width: 55vw;
    height: 90%;
    background-color: white;
    border-radius: 15px;
    padding: 10px;
}

section{

    width: 100%;
    height: 100%;
}
        
 .categories_container section:nth-child(even){  /* vilket barn vill vi styla? */
    background-color: rgba(0, 0, 0, 0.1) /* svart bakgrund med 10% opacitet */
}
 
  .categories_container section:nth-child(odd){  /* vilket barn vill vi styla? */
    background-color: rgba(0, 0, 0, 0.3) /* svart bakgrund med 30% opacitet */
}

.add-row {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
}
</style>

