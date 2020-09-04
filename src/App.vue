<template>
  <div id="app">
    <quotes-progress v-bind:quotes="quotes"></quotes-progress>
    <quotes-field v-on:add_quote="pushQuote"></quotes-field>
    <div class="quotes">
      <quotesLabel width="25%"
        v-for="(quote, position) in quotes"
        v-bind:position="position"
        v-on:click.native="quotes.shift(position);">
        {{ quote }}
      </quotesLabel>
    </div>
    <div class="info">
      <span>info: Click on a Quote to delete it!</span>
    </div>
  </div>
</template>

<script>

import QuotesField from './Quotes/QuotesField.vue'
import QuotesLabel from './Quotes/QuotesLabel.vue'
import QuotesProgress from './Quotes/QuotesProgress.vue'

export default {
  components:{
    'quotes-field': QuotesField,
    'quotesLabel': QuotesLabel,
    'quotes-progress': QuotesProgress
  },
  data : function() {
    return {
      quotes : []
    }
  },
  methods:{
    pushQuote : function(quote){
      if(this.quotes.length<10)
      this.quotes.push(quote);
    },
  }
};
</script>

<style>
#app{
  max-width: 1000px;
  margin: auto;
}
.info{
  background-color: #ddf0ff;
  text-align: center;
  padding-top: 1em;
  padding-bottom: 1em;
  border: 1px solid #acd;
  border-radius: 3px;
}
*{
  font-family: sans-serif;
  box-sizing: border-box;  
}
.quotes{
  margin-bottom: 10px;
}
</style>
