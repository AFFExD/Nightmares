

<script>

import ElizaBot from 'elizabot';
import { enhance } from "$app/forms";

const eliza = new ElizaBot();

let chat = $state([{ user: 'Eliza', message: eliza.getInitial() }]);

async function write(message) {

	chat.push({ user: 'User', message: message });

	const typingIndicator = document.getElementById("visible");

	if (typingIndicator) {
		typingIndicator.style.display = "flex";
	}


	await new Promise((r) => setTimeout(r, 1000 + Math.random() * 1000));

	chat.push({ user: 'Eliza', message: eliza.transform(message) });

	if (typingIndicator) {
		typingIndicator.style.display = "none";
	}
}

</script>

<main>
	<section>
		{#each chat as msg}
			<article class={msg.user}>
				<p>{msg.message}</p>
			</article>
		{/each}
		<article id="visible">
			<span class="circle"></span>
			<span class="circle"></span>
			<span class="circle"></span>
		</article>
	</section>
	
	<form method="post"
		use:enhance={({ formElement, formData, cancel }) => {
			cancel();
			const text = formData.get("text");
			write(text);

			formElement.reset();
		}}>
		<input type="text" name="text" placeholder="Skriv ditt meddelande.." />
	</form>
</main>

<style>

	.Eliza{
		background-color: #d1e7fd;
		align-self: start;
	}
	.User{
		background-color: #c8f7dc;
		align-self: end;
		text-align: right;
	}
	main {
		width: 60vw;
		height: 70vh;
		margin: auto;
		padding: 10px;
		background-color: #f0f4f8;
		display: grid;
		grid-template-rows: 90% 10%;
	}

	section {
		overflow-y: scroll;
		display: flex;
		flex-direction: column;
	}

	article, input {
		margin: 10px;
		padding: 10px;
		border-radius: 10px;
		background-color: #ffffff;
		width: 60%;
	}

	#visible {
		width: 100px;
		height: 60px;
		padding: 0;
		display: none;
		display: flex;
		align-items: center;
		gap: 5px;
		justify-content: center;
	}

	.circle {
		width: 10px;
		height: 10px;
		border-radius: 50%;
		background-color: #4a90e2;
		animation: typing 1000ms ease-in-out infinite;
	}

	@keyframes typing {
		0% {
			transform: scale(1);
		}
		50% {
			transform: scale(1.4);
		}
		100% {
			transform: scale(1);
		}
	}

	
            /* CSS-stilar för .circle med index 1 (den första cirkeln) */
            .circle:nth-child(1) {
                animation-delay: 0ms; /* Ingen fördröjning */
            }
            /* CSS-stilar för .circle med index 2 (den andra cirkeln) */
            .circle:nth-child(2) {
                animation-delay: 333ms; /* Starta animationen efter 333 millisekunder (ms) */
            }
            /* CSS-stilar för .circle med index 3 (den tredje cirkeln) */
            .circle:nth-child(3) {
                animation-delay: 666ms; /* Starta animationen efter 666 ms */
            }
            
</style>