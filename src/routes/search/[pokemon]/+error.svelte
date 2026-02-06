<script>
  import { page } from '$app/stores';
</script>

<section>
  <h1>You searched for: {$page.params.pokemon}</h1>
  <hr />
  <h2>{$page.status}: {$page.error.message}</h2>
</section>

<style>
  section {
    text-align: center;
    padding: 2em;
  }

  h1 {
    color: #3b4cca;
    margin-bottom: 1em;
  }

  hr {
    width: 50%;
    margin: 1em auto;
    border: 1px solid #ffcb05;
  }

  h2 {
    color: #c00;
  }
</style>
