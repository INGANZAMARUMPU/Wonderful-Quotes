<template>
  <div id="app">
    <h2>IMYIBUTSA Y'IKIRUNDI</h2>
    <quotes-progress v-bind:quotes="quotes"></quotes-progress>
    <div class="quotes">
      <quotesLabel
        v-for="(quote, position) in quotes"
        v-bind:position="position"
        v-on:close="e => remove(e, position)">
        {{ quote }}
      </quotesLabel>
    </div>
    <div class="info">
      <div>Menya Neza:
        <ul>
          <li>
            Ntushobora gushiramwo umwibutsa ugaragara!
          </li>
          <li>
            Ufyonze ku kamenyetso &times uba uhanaguye umwibutsa!
          </li>
          <li>
            Usigaje gushiramwo imyibutsa {{ 10 - this.quotes.length }}
          </li>
        </ul>
      </div>
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
    remove(event, position){
      event.target.closest('h3').classList.add("hidden")
      setTimeout(() => {
        event.target.closest('h3').classList.remove("hidden")
        this.quotes.splice(position, 1)
      }, 1000)
    }
  }
};
</script>

<style>
#app{
  max-width: 1000px;
  margin: auto;
}
h2{
  text-align: center;
}
.info{
  background-color: #ddf0ff;
  color: #5590aa;
  padding-top: 1em;
  padding-bottom: 1em;
  border: 1px solid #acd;
  border-radius: 3px;
  padding: 10px 40px 0 40px;
}
*{
  font-family: sans-serif;
  box-sizing: border-box;  
}
.quotes{
  width: 100%;
  margin-bottom: 10px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}
.hidden{
  opacity: 0;
  transition: opacity 1s;
}
</style>
