<template>
  <div>
      <div @click="deleteQuote(quote)" class="quote" v-for="(quote, key, iteration) in quotes" :key="iteration">
        <p>{{ quote.quote }}</p>
      </div>
  </div>
</template>

<script>
export default {
  props: ['quotes'],

  methods: {
    deleteQuote(quote) {
      this.$emit('deletedQuote', quote);
    }
  }
}
</script>

<style>
  .quote{
    display: inline-block;
    padding: 10px 30px;
    margin: 3px;
    background-color: rgb(223, 174, 13);
    border-radius: 10px;
    width: 49%;
    text-align: center;
  }
  .quote:hover{
    background-color: red;
    cursor: pointer;
  }
</style>