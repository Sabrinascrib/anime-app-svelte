
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

function handleOnSubmit() {
      fetch(`https://api.jikan.moe/v4/anime?q=${name}&sfw`)
      .then(response => response.json())
       .then(result => animes = result.data)
  }
</script>

<main>
<nav>
  <div class="logo">
       <h2>ramen n' chill</h2>
  </div>
  <form on:submit|preventDefault={handleOnSubmit}>  <input type="text" name="name" bind:value={name} placeholder="Search for an anime...">
    <button type="submit"><svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" preserveAspectRatio="xMidYMid meet" viewBox="0 0 24 24"><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-width="2" d="m21 21l-4.486-4.494M19 10.5a8.5 8.5 0 1 1-17 0a8.5 8.5 0 0 1 17 0Z"/></svg></button>
  </form>
</nav>
<h4>Animes</h4>
<div class="animes">
{#each animes as anime (anime.mal_id)}
<div class="anime">
  <!-- <img src="anime.images.jpg.large_image_url" alt="{anime.title}"> -->
   <img src="./images/naruto-shippuden-group-i129089.jpg" alt="{anime.title}">
  <h2>{anime.title}</h2><p>{anime.aired.string}</p>
</div>
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



  .logo h2  {
    color: #000;
    font-weight: 300;
    text-transform: uppercase;
  }

  form {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }


        input { 
          height: 30px;
    width: 200px;
    border: solid #000000 2px;
    background-color: #fff;
    padding: 2px 10px 2px 1px;
        border-top-style: hidden;
        border-right-style: hidden;
        border-left-style: hidden;
      }
      
      input:focus {
        outline: none;
      }

      button {
        height: 36px;
    border: solid #000000 2px;
    background-color: #fff;
    padding: 2px 10px;
        border-top-style: hidden;
        border-right-style: hidden;
        border-left-style: hidden;
        margin-left: 10px;
      }

      button svg {
        font-size: 17px;
      }

      h4 {
        font-size: 15px;
        text-align: center;
        margin-top: 100px;
            font-weight: 500;
      }

  .animes {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
    max-width: 1500px;
    margin: 40px auto 0 auto;

  }

  .anime {
    display: flex;
    flex-direction: column;
    background-color: #fff;
    width: 200px;
    height: 390px;
    margin: 0px 20px 40px 20px;
    border: #fff solid 10px;
    
  }

  .anime img {
    width: 200px;
    border-radius: 10px;
  }

  .anime h2 {
    font-size: 13px;
    font-weight: 700;
    margin: 10px 0 0 0 ;

  }

  .anime p {
    font-size: 10px;
color: #686868;
font-weight: 400;
margin: 5px 0 0 0;
  }


</style>