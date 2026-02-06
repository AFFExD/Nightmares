<script>
  // Importera goto-funktionen för att navigera mellan sidor
  import { goto } from '$app/navigation';
  
  // Funktion som hanterar formulärets submit-händelse
  function handleSubmit(e) {
    // Förhindra att sidan laddas om (standardbeteende för formulär)
    e.preventDefault();
    
    // Skapa ett FormData-objekt från formuläret
    const formData = new FormData(e.target);
    
    // Hämta värdet från input-fältet med name="search"
    const search = formData.get('search');
    
    // Navigera till den dynamiska routen /search/[pokemon]
    goto('search/' + search);
  }
</script>

<form onsubmit={handleSubmit}>
  <input type="text" name="search" placeholder="Sök upp en pokemon" />
</form>

<style>
  form {
    width: 100%;
    display: flex;
    justify-content: center;
    padding: 2em;
  }

  input {
    width: 60%;
    padding: 1em;
    font-size: 1.2em;
    border: 2px solid #3b4cca;
    border-radius: 10px;
    outline: none;
    transition: all 0.3s ease;
  }

  input:focus {
    border-color: #ffcb05;
    box-shadow: 0 0 10px rgba(255, 203, 5, 0.5);
  }
</style>
