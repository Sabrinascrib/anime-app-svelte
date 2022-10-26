<script>
  let animes = []

  fetch('https://api.jikan.moe/v4/anime?q=naruto&sfw')
  .then(response => response.json())
  .then(data => console.log(data))
</script>