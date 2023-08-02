<script>
  let promise = fetch("https://dog.ceo/api/breeds/image/random")
  const getNewDogImage = () => {
    promise = fetch("https://dog.ceo/api/breeds/image/random")
  }
</script>

<header>
  <h1>Randomz Dog</h1>
</header>
<main>
<div>
<button on:click={getNewDogImage}>Get different dog</button>
  <h2>Look at this cute dog</h2>
  {#await promise}
    <p>Fetching...</p>
  {:then response}
    {#await response.json()}
      {:then data}
      <img src={data.message} alt="Dog's image">
      {:catch error}
      <p>Failed to fetch, error occured</p>
    {/await}
  {:catch error}
    <p>Failed to fetch, error occured</p>
  {/await}
</div>
</main>

<style>
img {
  width: 100%;
  border: 3px solid white;
  border-radius: 4px;
}
</style>