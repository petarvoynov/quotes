<template>
  <div>
      <h2>Quotes Added</h2>
      <div class="counter-bar">
        <div v-if="quotesCount" class="progress-counter-bar" :style="{width: quotesCount * 10 + '%'}">{{ quotesCount }} / 10</div>
        <p class="progress-counter-bar" v-else>There are no quotes!</p>
      </div>
  </div>
</template>

<script>
export default {
  props: ['quotesCount'],
}
</script>

<style>
  .counter-bar {
    width: 100%;
    background-color: rgb(204, 212, 228);
    border-radius: 10px;
  }
  .progress-counter-bar{
    padding: 5px 10px;
    background-color: rgb(62, 117, 219);
    border-radius: 10px;
    width: 100%;
    color: white;
  }
</style>