<main>

    <div class="container">
    <h1>Shopping List</h1>
    <!-- Innehåll för shoppinglistan går här -->
     <div class="categories_container">
        <section></section>
        <section></section>

        <!-- Kategorier för shoppinglistan går här -->
     </div>
    </div>
    
    <style>

.container{
    background-color: #f0f0f0;
    display: grid;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 60vw;
    height: 70vh;
    border-radius: 20px;
    grid-template-rows: 1fr 8fr 1fr;
}
        
.categories_container{
    display: grid;
    grid-template-columns: 2,1fr;
    gap: 20px;
    width: 90%;
    height: 90%;
    background-color: white;
    border-radius: 15px;
    padding: 10px;
}
        
</style>

</main>