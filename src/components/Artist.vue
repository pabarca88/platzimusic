<template>
  <li>
    <h2>
      <a :href="artist.url" target="_blank">{{ artist.name }}</a>
    </h2>
    <!-- <img :src="artist.image[2]['#text']" alt=""> -->
  </li>
</template>

<script>
export default {
  name: 'artist',
  props: [ 'artist' ]
}
</script>

<style>
li{
  margin: 10px 0 0;
  font-size: 14px;
}
li h2{
  margin: 0;
}
</style>
