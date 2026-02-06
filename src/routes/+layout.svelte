<script>
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
import { base } from '$app/paths';
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<nav>
	<a href="{base}/">start</a>

<a href="{base}/Photoapp">Photoapp</a>

<a href="{base}/Register">Register</a>

<a href="{base}/Shoppinglist">Shoppinglist</a>

<a href="{base}/prov">prov</a>

<a href="{base}/Memory">Memory</a>

<a href="{base}/chat">chat</a>

<a href="{base}/search">search</a>

</nav>


{@render children?.()}


<style>
:global(body), :global(html){
  margin: 0%;
  padding: 0%;
  height: 100vh;
  width: 100vw;
}    
</style>