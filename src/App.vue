<template>
  <div class="container">
    <app-bar :quotesCount="quotesCount" :maxCount="maxCount"></app-bar>
    <app-form @quoteAdded="addQuote" :quotesCount="quotesCount" :lastQuoteId="lastQuoteId" :maxCount="maxCount"></app-form>
    <app-list :quotes="quotes" @deletedQuote="deleteQuote"></app-list>
    <app-info></app-info>
  </div>
</template>

<script>
  import Bar from './components/Quote/Bar.vue';
  import Form from './components/Quote/Form.vue';
  import Info from './components/Quote/Info.vue';
  import List from './components/Quote/List.vue';
export default {
  components: {
    'app-bar': Bar,
    'app-form': Form,
    'app-info': Info,
    'app-list': List
  },
  data(){
    return {
      quotes: [],
      maxCount: 10,
    }
  },
  methods: {
    addQuote(quote){
      this.quotes.unshift(quote);
    },
    deleteQuote(quote){
      this.quotes = this.quotes.filter(q => quote.id != q.id);
    },
  },
  computed: {
    quotesCount(){
      return this.quotes.length;
    },
    lastQuoteId(){
      if(this.quotesCount <= 0){
        return 0;
      } else {
        return this.quotes[0].id;
      }
    }
  }
}
</script>

<style>
  *{
    box-sizing: border-box;
  }
  .container {
    width: 70%;
    margin: auto;
    padding: 30px;
    background-color:rgb(246, 246, 246);
  }
</style>
