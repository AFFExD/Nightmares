<script>
	import { goto } from '$app/navigation';

	function handleSubmit(e) {
		e.preventDefault();
		const formData = new FormData(e.target);
		const search = formData.get('search');
		goto('/search/' + search);
	}
</script>

<div class="backdrop"></div>
<main>
	<h1>Snart ska vi söka efter pokemons!</h1>
	<form onsubmit={handleSubmit}>
		<input type="text" name="search" placeholder="Sök upp en pokemon" />
	</form>
	<slot />
</main>

<style>
	.backdrop {
		width: 100vw;
		height: 100vh;
		background-image: url('https://imageio.forbes.com/specials-images/imageserve/604202ff091b6539cb90fcbc/The-backs-of-a-number-of-Pok-mon-cards-/960x0.jpg?format=jpg&width=960');
		background-size: cover;
		position: fixed;
		top: 0;
		left: 0;
		z-index: -1;
		filter: blur(5px);
	}

	main {
		width: 80vw;
		height: 100vh;
		background-color: rgba(255, 255, 255, 0.8);
		margin: 5vh auto;
		border: 1px solid #ccc;
		border-radius: 8px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	form {
		display: flex;
		gap: 10px;
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
</style>
