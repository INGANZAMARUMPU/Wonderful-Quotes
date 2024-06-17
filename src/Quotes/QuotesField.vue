<template>
  <div id="main">
  	<div class="field">
  		<input type="text" v-model="quote" placeholder="Andikamwo umwibutsa"/>
  		<button v-on:click="addQuote">Ongeramwo</button>
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
		addQuote(){
			console.log(this.quote.split(" ").length)
			if(this.quote.split(" ").length < 2){
				this.$emit("error");
				this.quote = "";
			} else {
				this.$emit("add_quote", this.quote);
				this.quote = "";
			}
		}
	}
};
</script>
<style scoped>
.field{
	display: flex;
	gap: 10px;
}
input{
	flex-grow: 1;
	border: 2px solid #48b;
	border-radius: 3px;
	padding: 0 20px;
}
button{
	background-color: #48b;
	padding: 10px 30px;
	color: white;
	border-radius: 3px;
	border: 0;
}
</style>
