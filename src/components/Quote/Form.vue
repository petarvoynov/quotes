<template>
  <div>
    <div class="form">
      <form @submit.prevent="addQuote">
        <label for="quote">Quote</label>
        <textarea id="quote" cols="80" rows="5" placeholder="Add a quote" v-model="quote" @keydown="showTheButton"></textarea>
        <p v-for="(error, index, iteration) in errors" :key="iteration">{{ error }}</p>
        <button v-if="showButton">Add Quote</button>
      </form>
    </div>   
  </div>
</template>

<script>
export default {
  props: ['quotesCount', 'lastQuoteId', 'maxCount'],
  data(){
    return {
      quote: '',
      showButton: true,
      errors: []
    };
  },
  methods: {
    addQuote(){
      if(this.quote == ''){
        this.errors.unshift('You cannot add an empty quote!');
        this.showButton = false;
        return;
      }
      if(this.quotesCount >= this.maxCount){
        return alert(`You cannot have more than ${this.maxCount} quotes! Please remove some to add new ones.`);
      } else {
        let quote = {
          'id': this.lastQuoteId + 1,
          'quote': this.quote
        }
        this.$emit('quoteAdded', quote);
        this.quote = '';
      }
    },
    showTheButton(){
      this.showButton = true;
      this.errors = [];
    }
  }
}
</script>

<style>
  .form {
    margin: 20px;
    text-align: center;
  }
  label{
    display: block;
    text-align: left;
    width: 50%;
    margin: 10px auto;
  }
  button{
    display: block;
    margin: 15px auto;
    padding: 10px 20px;
    border-radius: 10px;
    background-color: rgb(62, 117, 219);
    color: white;
    border: none;
    cursor: pointer;
  }
  button:hover {
    background-color: rgb(51, 104, 202);
  }
  textarea {
    width: 50%;
    padding: 10px;
  }
</style>