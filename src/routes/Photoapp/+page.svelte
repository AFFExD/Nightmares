<div class="photos">
    <div class='image-wrapper'>
        <img src="https://i.redd.it/rofzm44oka091.png" alt="bild information">
    </div>
        <div class='image-wrapper'>
        <img src="https://i.redd.it/vd9dc7wfk9471.png" alt="bild information">
    </div>
        <div class='image-wrapper'>
        <img src="https://miro.medium.com/v2/resize:fit:1400/0*YeaUsQyhXSL1TCTH.png" alt="bild information">
    </div>


</div>
<style>
    .photos{
        display:flex;
        justify-content: center;
        align-items: center;

        max-width: 90vw;
    }

    .image-wrapper{
        flex: 1;
    }

    .image-wrapper img{
        width: 100%;
        height: auto;
        border-radius: 10px;
        margin:10px;
    }

    .image-wrapper:hover{ 
        flex:2; 
        
    }

    .image-wrapper:active { 
        transform: scale(0.9); 
    
    }
</style>
