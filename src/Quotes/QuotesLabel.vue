<template>
	<div v-bind:style="{width:width}">
		<h3>
			<span class="icon">"</span>
			<slot>no text</slot>
		  <div class="close" @click="e => $emit('close', e)">&times</div>
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
  h3{
	  color: var(--primary);
	  font-style: italic;
	  margin: 0;
	  position: relative;
	  background-color: #FAFAFA;
	  padding: 40px 20px 20px 30px;
  }
  h3:hover{
	background-color: #EEE;
  }
  .close{
	  color: red;
	  position: absolute;
	  top: 2px;
	  right: 10px;
  }
  .close:hover{
	  cursor: default;
	  text-shadow: 0 0 10px red;
  }
  .icon{
	top:10px;
	left: 10px;
	position: absolute;
	font-size: 3em;
  }
  </style>
  