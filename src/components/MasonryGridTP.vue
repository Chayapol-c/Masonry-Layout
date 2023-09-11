<script setup>

const props = defineProps({
  imageList: []
});

</script>
<template>
  <div class="masonry-grid">
    <div
      v-for="(image, index) in props.imageList"
      :key="index"
      class="masonry-item"
    >
      <img :src="image.url" alt="Image" />
    </div>
  </div>
</template>

<style scoped>
.masonry-grid {
  display: grid;
  gap: 10px;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-template-rows: masonry;
  
  counter-reset: box;
}

.masonry-item {
  position: relative;
}

.masonry-item::before {
  counter-increment: box;
  content: counter(box);
  top: 50%;
  left: 50%;
  transform: translateX(-8px);
  background-color: black;
  position: absolute;
  padding: 4px;
}

</style>