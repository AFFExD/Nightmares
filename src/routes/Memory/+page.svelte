<h1>Memory</h1>
<h2>{currentPlayer === 'blue' ? 'Blå spelares tur' : 'Röd spelares tur'}</h2>
<main>

    {#each cards as card}
        <div class="card" class:flipped={card.flipped } onclick={() => flipCard(card)}>
            <img src="{card.img}" class="front" alt="Card image"/>
            <img src="{back_img}" class="back" alt="Card back"/>
        </div>
    {/each}
</main>

<aside class='blue' class:turn={currentPlayer === 'blue'}>
    <p> {bluePoints} </p>
    </aside>
<aside class:turn={currentPlayer === 'red'}>
<p> {redPoints} </p>
</aside>




<style>
h1{
    text-align: center;
}

.card{
    width: 100%;
    height: 100%;
    position: relative;
    transform-style: preserve-3d;
    transition: transform 0.5s;
}


.front, .flipped{
    transform: rotateY(180deg);
}
.card img{
    width: 100%;
    height: 100%;
    position: absolute;

    backface-visibility: hidden;}


    main{
        justify-content: center;
        display: grid;
        grid-template-columns: repeat(4, 100px);
        grid-template-rows: repeat(3, 100px);
        gap: 10px;
        width: 800px;
        height: 800px;
        margin: auto;
        background-color: lightgray;
    }

    
    aside{
    width: 100px;
    height: 100px;
    position: fixed;
    bottom: 10px;
    right: 10px;
    background-color: red;
    display: flex;
    justify-content: center;
    align-items: center;
    }
    .blue{
        left:10px;
    background-color: blue;
    }
   p{
    font-size: 30px;
    }
    
    aside{

    }
    .turn{
        border: 5px solid yellow;
        z-index: 1;
    }
</style>

<script>
    let imgs = [
        "https://upload.wikimedia.org/wikipedia/en/7/73/Arc_Raiders_cover_art.jpg", // ARC
        "https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/252490/capsule_616x353.jpg", // Rust
        "https://upload.wikimedia.org/wikipedia/en/4/4f/TLOU_P2_Box_Art_2.png", // Tlou 2
        "https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/FortniteLogo.svg/200px-FortniteLogo.svg.png", // Fortnite
        "https://upload.wikimedia.org/wikipedia/commons/thumb/f/f2/Roblox_%282025%29_%28App_Icon%29.svg/250px-Roblox_%282025%29_%28App_Icon%29.svg.png", // Roblox
        "https://cdn.cloudflare.steamstatic.com/steam/apps/518790/header.jpg" // theHunter
    ];
    let back_img ="https://cdn-icons-png.flaticon.com/512/709/709586.png";
    let bluePoints = $state(100);
    let redPoints = $state(100);
    let currentPlayer = $state('blue');
    const cards = $state([])
    for (let i = 0; i < 12; i++) {
        cards.push({img:imgs[i%6],flipped:false,matched:false});
    }


    function flipCard(card){
        if(!card.flipped && !card.matched){
            card.flipped = true;


            const flippedCards = cards.filter(c => c.flipped && !c.matched);

            if (flippedCards.length === 2) {


                if (flippedCards[0].img === flippedCards[1].img) {
                    flippedCards[0].matched = true;
                    flippedCards[1].matched = true;
                    // Ingen turväxling vid match
                } else {
                    // Dra av poäng för aktuell spelare om det inte är en match
                    if (currentPlayer === 'blue') {
                        bluePoints = Math.max(0, bluePoints - 10);
                    } else {
                        redPoints = Math.max(0, redPoints - 10);
                    }
                    // Växla spelare
                    currentPlayer = currentPlayer === 'blue' ? 'red' : 'blue';
                }
                setTimeout(() => {
                    cards.forEach((card) => {
                        card.flipped = card.matched;
                    });
                    }, 1000);
                                
            }
        }
        
    }
</script>