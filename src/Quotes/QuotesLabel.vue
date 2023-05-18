<template>
	<div v-bind:style="{width:width}">
		<h3>
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
	  background-color: #dfd;
	  color: #7a7;
	  border: 2px solid #7a7;
	  border-radius: 5px; 
	  font-style: italic;
	  padding: 1em;
	  word-break: break-all;
	  box-shadow: 0 0 2px#7a7;
	  display: flex;
	  justify-content: space-between;
	  margin: 0;
  }
  h3:hover{
	  background-color: #fee;
	  border: 2px solid #a77;
	  color: #a77;
	  box-shadow: 0 0 5px#a77;
  }
  .close{
	  display: none;
  }
  h3:hover .close {
	  display: block;
  } 
  .close:hover{
	  cursor: default;
	  color: red;
	  text-shadow: 0 0 10px red;
  }
  </style>
  