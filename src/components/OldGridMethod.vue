<script setup>
const props = defineProps({
  imageList: []
});

</script>

<template>
  <div class="masonry-grid">
    <template v-for="(item, index) in imageList" :key="index">
      <figure class="box">
        <img :src="item.url" alt="">
      </figure>
    </template>
  </div>
</template>

<style scoped>
.masonry-grid {
  counter-reset: box;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-auto-rows: 1fr;
  grid-auto-flow: dense;
  grid-gap: 5px;
  max-width: 1080px;
  height: 100vh;
  margin: 0 auto;
}

.box {
  margin: 0;
  display: flex;
  flex-direction: column;
  position: relative;
}

.box::before {
  counter-increment: box;
  content: counter(box);
  top: 50%;
  left: 50%;
  transform: translateX(-16px);
  background-color: black;
  position: absolute;
  padding: 4px;
}

.box>img {
  flex: 1;
  max-width: 100%;
  object-fit: cover;
}

.box>figcaption {
  padding: 0.5rem 1rem;
  background-color: #48cfad;
  color: #fff;
  text-align: center;
}


.box:nth-child(2n + 1) {
  grid-row: span 2;
  grid-column: span 2;
}

/* .box:nth-child(4n + 1) {
  background-color: #48cfad;
}

.box:nth-child(4n + 2) {
  grid-row: span 2;
  grid-column: span 2;
  background-color: #4fc1e9;
}

.box:nth-child(4n + 3) {
  background-color: #ed5565;
}

.box:nth-child(4n + 4) {
  grid-row: span 2;
  grid-column: span 2;
  background-color: #ac92ec;
} */
</style>