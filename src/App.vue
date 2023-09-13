<script setup>
import { onMounted, reactive, ref } from 'vue';
import MasonryColumn from './components/MasonryColumn.vue';
import MasonryGridTP from './components/MasonryGridTP.vue';
import MasonryGrid from './components/MasonryGrid.vue';
const imageList = reactive([])

const methodList = ['grid', 'grid-tp', 'column']
const currentMethod = ref('grid')

async function getImages(width, height) {
  const response = await fetch(`https://picsum.photos/seed/picsum/${width}/${height}`)
  const data = await response?.url;
  imageList.push({url: data, height})
}

function updateMethod(e) {
  currentMethod.value = e.target.value
}

function randomNumber(min, max) {
  return Math.floor(Math.random() * (max - min) + min);
}

onMounted(() => {
  for (let i = 0; i < 30; i++) {
    getImages(200, randomNumber(2, 6) * 100)
  }
});
</script>

<template>
  <main>
    <h1>Masonry Grid use case</h1>
    <div class="radio-group">
      <template v-for="(method, index) in methodList" :key="index">
        <div>
          <input type="radio" :value="method" :checked="method === currentMethod" @change="updateMethod">
          <label :for="method">{{ method }}&nbsp;<span v-if="method === 'grid-tp'">(only work on safari)</span> </label>
        </div>
      </template>
    </div>
    <MasonryGrid v-if="currentMethod === 'grid'" :imageList="imageList" />
    <MasonryGridTP v-if="currentMethod === 'grid-tp'" :imageList="imageList" />
    <MasonryColumn v-if="currentMethod === 'column'" :imageList="imageList" />
  </main>
</template>

<style scoped>
h1 {
  text-align: center;
}
.radio-group {
  max-width: 720px;
  margin: 3rem auto;
}
.radio-group > div {
  display: flex;
  column-gap: 1rem;
  margin-bottom: 1rem;
}
</style>
