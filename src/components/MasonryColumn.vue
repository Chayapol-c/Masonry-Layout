<script setup>

const props = defineProps({
  imageList: []
});

</script>

<template>
  <div class="container">
    <figure v-for="(image, index) in props.imageList" :key="index">
      <img :src="image.url" alt="">
      <figcaption>{{ index + 1 }}</figcaption>
    </figure>
  </div>
</template>

<style scoped>
img {
  max-width: 100%;
  display: block;
}

figure {
  margin: 0;
  display: grid;
  grid-template-rows: 1fr auto;
  margin-bottom: 10px;
  break-inside: avoid;

  position: relative;
}

figure>img {
  grid-row: 1 / -1;
  grid-column: 1;
}

figcaption {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-8px);
  background-color: black;
  position: absolute;
  padding: 4px;
}

.container {
  column-count: 5;
  column-gap: 0.5rem;
  margin: 0 auto;
  max-width: 1080px;
}
</style>