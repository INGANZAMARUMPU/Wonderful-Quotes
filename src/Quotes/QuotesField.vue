<template>
  <div id="main">
  	<h3>Quotes</h3>
  	<div>
  		<textarea v-model="quote"></textarea>
  	</div>
  	<div>
  		<button v-on:click="addQuote">Add Quote</button>
  	</div>
  </div>
</template>
<script>
export default {
	data: function (){
		return {
			quote:""
		}
	},
	methods: { 
		addQuote : function (){
			if(this.quote != "")
			this.$emit("add_quote", this.quote);
			this.quote = "";
		}
	}
};
</script>
<style scoped>
#main{
	width: 500px;
	margin: auto;
	padding: 5px;
}
h3{
	margin: 0;
}
textarea{
	height: 70px;
	width: 100%;
}
button{
	position: relative;
	background-color: #48b;
	padding: 10px 1em;
	color: white;
	border-radius: 5px;
	border: 1px solid #259;
	font-weight: bold;
	left:50%;
	transform: translate(-50%, 0);
}
</style>
