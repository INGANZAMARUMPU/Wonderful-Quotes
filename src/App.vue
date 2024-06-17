<template>
  <div id="app">
    <h2>IMYIBUTSA Y'IKIRUNDI</h2>
    <quotes-progress :quotes="quotes" v-if="quotes.length > 0"></quotes-progress>
    <quotes-field @add_quote="pushQuote" @error="display_error"/>
    <div class="info" v-show="!!error">
      <div>Menya Neza:
        <ul>
          <li>Nta mwibutsa ugira amajambo ari musi y'abiri!</li>
          <li>Ufyonze ku kamenyetso &times uba uhanaguye umwibutsa!</li>
          <li>Usigaje gushiramwo imyibutsa {{ 10 - this.quotes.length }}</li>
        </ul>
      </div>
    </div>
    <div class="quotes">
      <quotesLabel
        v-for="(quote, position) in quotes"
        :position="position"
        @close="e => remove(e, position)">
        {{ quote }}
      </quotesLabel>
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
      quotes: [],
      error: false
    }
  },
  methods:{
    pushQuote : function(quote){
      if(this.quotes.length<10)
      this.quotes.push(quote);
    },
    display_error(){
      this.error = true
      window.setTimeout(() => {
        this.error = false
      }, 10000)
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
:root{
  --primary: #48b;
  --primary-hover: #48b;
  --danger: #A55;
  --danger-hover: #FDD;
}
#app{
  width: 90%;
  max-width: 1000px;
  margin: auto;
  display: flex;
  flex-direction: column;
  gap: 20px;
}
h2{
  text-align: center;
  color: var(--primary);
}
.info{
  background-color: var(--danger-hover);
  color: var(--danger);
  padding-top: 1em;
  padding-bottom: 1em;
  border: 1px solid var(--danger);
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
  display: flex;
  flex-direction: column;
  gap: 20px;
}
.hidden{
  opacity: 0;
  transition: opacity 1s;
}
</style>
