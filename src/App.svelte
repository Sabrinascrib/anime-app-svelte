
<script>
  import { onMount } from 'svelte'

  let animes = []

  onMount(() => {
    fetch('https://api.jikan.moe/v4/anime?q=naruto&sfw')
      .then(response => response.json())
       .then(result => animes = result.data)
	//   .then(result => console.log(result.data))
  })
</script>

{#each animes as anime (anime.mal_id)}

  <img src="anime.images.jpg.large_image_url" alt="{anime.title}">

  <h2>{anime.title}</h2>
{/each}