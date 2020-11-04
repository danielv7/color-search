<template>
 <div class="colorview">
   <section class="flex-container">
      <button v-for="color in colorToExpand" :key="color.id"  class="card" v-bind:style="{ backgroundColor: color.HexCode}">
        <div class="container">
          {{ color.HexCode }} 
        </div>
      </button>
    </section>
      <button style = "position:fixed; left:650px" class="btn" @click="handleClick()">Clear</button>
  </div>
</template>

<script>
  export default {
  name: 'detailview',
  props: {
    colorToExpand: Array,
  },
  methods:{
	handleClick () {	
        this.$emit('clear-color')
    },
  },
}
</script>

<style scoped>

.colorview {
  height: 85%; /* Full-height: remove this if you want "auto" height */
  width: 75%; /* Set the width of the sidebar */
  position: fixed; /* Fixed Sidebar (stay in place on scroll) */
  z-index: 1; /* Stay on top */
  top: 120px; /* Stay at the top */
  left: 300px;
  background-color: white; 
  overflow-x: hidden; /* Disable horizontal scroll */
  padding-top: 20px;
}
.flex-container {
  display: flex;
  flex-wrap: wrap;
  padding-bottom: 10px;
}
.card {
  outline: none;
  border: 1px solid black;
  width: 950px;
  height: 500px;
  border: 1px solid black;
  padding: 0px;
  position: relative;
  border-radius: 5px;
}
.container {
  font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  font-size: 20px;
  color: #404040;
  width: 100%;
  height: 15%;  
  background: white;
  position: absolute;
  bottom:0;
  display:flex;
  align-items: center;
  text-indent: 20%;
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
}
.btn {
  border: 1px solid black;
  background-color: white;
  color: #404040;
  font-size: 20px;
  border-radius: 10px;
  outline-color: black;
  margin-left: 10px;
  justify-content: center;
  line-height: 0;
  padding-left: 100px;
  padding-right: 100px;
  padding-top: 25px;
  padding-bottom: 25px;
}
</style>