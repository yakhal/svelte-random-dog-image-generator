<script>
  let imageUrl;
  let isError;
  const getNewDog = () => {
    fetch("https://dog.ceo/api/breeds/image/random")
      .then((response) => response.json())
      .then((data) => {
        imageUrl = data.message;
      }).catch(error => {
        isError = true;
      })
  }
  getNewDog();
</script>

<header>
  <h1>Randomz Dog</h1>
</header>
<main>
<div>
<button on:click={getNewDog}>Get different dog</button>
<h2>Look at this cute dog</h2>
{#if imageUrl === undefined}
  <p>Fetching...</p>
{:else if isError}
  <p>Some error occured, try again!</p>
{:else}
  <img src={imageUrl} alt="Dog's image">
{/if}
</div>
</main>

<style>
img {
  width: 100%;
  border: 3px solid white;
  border-radius: 4px;
}
</style>

