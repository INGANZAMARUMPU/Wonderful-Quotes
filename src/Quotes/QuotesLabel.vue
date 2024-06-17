<template>
	<div v-bind:style="{width:width}">
		<h3>
			<span style="font-size: 3em;">"</span>
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
	  color: #7a7;
	  font-style: italic;
	  word-break: break-all;
	  margin: 0;
	  position: relative;
	  background-color: #eee;
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
  </style>
  