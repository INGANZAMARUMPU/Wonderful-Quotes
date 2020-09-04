<template>
  <div>
  	<h1>Quotes Added</h1>
  	<div class="progress">
  		<div class="progression" v-bind:style="{width:computedWidth}">{{quotes.length}}/10</div>
  	</div>
  </div>
</template>
<script>
export default {
	props: { quotes:Array },
	computed: {
		computedWidth:function (){
			return this.quotes.length*10+"%";
		}
	}
};
</script>
<style scoped>
h1{
	margin-bottom: 0;
}
.progress{
	width: 100%;
	height: 25px;
	background-color: lightgray;
	margin : 10px 0;
	border-radius: 5px;
}
.progression{
	height: 100%;
	background-color: #48b;
	text-align: center;
	color: white;
	border-radius: 5px;
}
</style>
