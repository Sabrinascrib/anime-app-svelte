
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




</style>