<script setup>

const props = defineProps({
  imageList: []
});

</script>
<template>
  <div class="masonry-grid">
    <div v-for="(image, index) in props.imageList" :key="index" class="masonry-item"
      :style="{ gridRow: `span ${(image.height / 100)}` }">
      <img :src="image.url" alt="Image" />
    </div>
  </div>
</template>

<style scoped>
.masonry-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-auto-rows: minmax(100px, 110px);
  grid-auto-flow: dense;
  counter-reset: box;

  max-width: 1080px;
  height: 100vh;
  margin: 0 auto;
}

.masonry-item {
  position: relative;
  overflow: hidden;
  margin: 10px;
  box-sizing: border-box;
}

.masonry-item::before {
  counter-increment: box;
  content: counter(box);
  top: 50%;
  left: 50%;
  transform: translate(-8px);
  background-color: black;
  position: absolute;
  padding: 4px;
}

.masonry-item img {
  max-width: 100%;
  height: auto;
  display: block;
}
</style>