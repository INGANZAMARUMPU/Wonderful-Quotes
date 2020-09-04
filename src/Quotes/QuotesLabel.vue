<template>
  <div id="main" v-bind:style="{width:width}">
  	<h3>
  		<slot>no text</slot>
  	</h3>
  </div>
</template>
<script>
export default {
	props :{
		position:{
			type : Number,
			default : -1
		},
		width : String
	}
};
</script>
<style scoped>
#main{
	display: inline-block;
}
h3{
	color: gray;
	border: 2px solid lightgray;
	border-radius: 5px; 
	font-style: italic;
	padding: 1em;
	margin: 5px;
	word-break: break-all;
}
h3:hover{
	background-color: #fee;
}
</style>
