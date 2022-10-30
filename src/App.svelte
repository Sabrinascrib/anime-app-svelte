
<script>
  import { onMount } from 'svelte'
	let name = '';
  let animes = []

  onMount(() => {
    fetch(`https://api.jikan.moe/v4/anime?q=${name}&sfw`)
      .then(response => response.json())
       .then(result => animes = result.data)
	  // .then(result => console.log(result.data))
  })
</script>

<main>
<nav>
  <div class="logo">
      <img src="./images/mie.png" alt="ramen logo" /> <h2>ramen <span> n' chill</span></h2>
  </div>
  <input bind:value={name} placeholder="Search for an anime...">
</nav>

<div class="animes">
{#each animes as anime (anime.mal_id)}
<div class="anime">
  <!-- <img src="anime.images.jpg.large_image_url" alt="{anime.title}"> -->
   <img src="./images/naruto-shippuden-group-i129089.jpg" alt="{anime.title}">
<p>{anime.title_japanese}</p>
  <h2>{anime.title}</h2></div>
{/each}

</div>

</main>
<style>

main {
  font-family: 'Poppins', sans-serif;
}

  nav {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    padding: 0px 50px;
    align-items: center;
    max-width: 1500px;
    margin: 0 auto;
  }

  .logo {
    display: flex;
    flex-direction: row;
    align-items: center;
  }

  .logo img {
    width: 50px;
    height: 50px;
    margin-right: 10px;
    margin-bottom: 10px;
  }

  .logo h2 span {
    color: #33cccc;
    font-style: italic;
  }

  input {
    height: 30px;
    width: 200px;
    border: solid #e0e0e0 1px;
    background-color: #f1f1f1;
    padding: 2px 10px;
    border-radius: 5px;
  }

  input:focus {
border: solid #33cccc 1px;
  }


</style>