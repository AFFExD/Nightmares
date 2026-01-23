
<div class="container">

   <section>1</section>
   <section>2</section>
   <section>3</section>
   <section>4</section>
   <section>5</section>
   <section>6</section>
</div>

<style>
 section:nth-child(1){
    background-color: aliceblue;
 }
    .container{
        display: grid;
        grid-column: 3;
        grid-template-columns:repeat(3, 1fr);;
        grid-template-rows: auto;
        column-gap: 25px;
        width: 900px;
        height: 500px;
        background-color: lightgray;
        align-content: space-around;
        align-items: flex-start;
    }

    section{
        background-color: green;
        display: grid;
        grid-template-rows: 200px;
        align-items: center;
        justify-content: center;
    }

    
    
</style>
