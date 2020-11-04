<template>
  <div class="colorview">
    <section class="flex-container">
      <button v-for="color in paginatedData" :key="color.id"  class="card" @click="handleClick(color.id)" v-bind:style="{ backgroundColor: color.HexCode}">
      <div class="container">
        {{ color.HexCode }} 
      </div>
      </button>
    </section>
    <ul class="vertical-center">
      <button @click="prevPage" :disabled="pageNumber==0">
        Previous
      </button>
      <div class="pagenum"> {{pageNumber + 1}} </div>
      <button @click="nextPage" :disabled="pageNumber==8">
        Next
      </button>
    </ul>	
  </div>
</template>

<script>
  export default {
  name: 'colorview',
  props: {
    cssColorData: Array,
    size: Number,
  },
  data () {
		return {
      pageNumber: 0,  // default to page 0
		}
  },
  methods:{
    handleClick (colorId) {
      this.$emit('send-color', colorId)
    },
    nextPage(){
      this.pageNumber++;
    },
    prevPage(){
      this.pageNumber--;
    },
	},
	computed: {
    pageCount(){
      let l = this.cssColorData.length,
          s = this.size;
      return Math.ceil(l/s);
    },
    paginatedData(){
      const start = this.pageNumber * this.size, end = start + this.size;
      return this.cssColorData.slice(start, end);
    },
	},

}
</script>

<style scoped>
.colorview {
  height: 80%; /* Full-height: remove this if you want "auto" height */
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
}
.card {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  outline: none;
  border: none;
  width: 225px;
  height: 250px;
  padding: 0px;
  position: relative;
  border-radius: 5%;
  margin: 20px;
}
.container {
  font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  font-size: 15px;
  color: #404040;
  width: 100%;
  height: 15%;  
  background: white;
  position: absolute;
  bottom:0;
  display:flex;
  align-items: center;
  text-indent: 10%;
  border-bottom-left-radius: 5%;
  border-bottom-right-radius: 5%;
}
button {
  background: black;
  margin: 2px;
  font-family: "Times New Roman", Times, serif;
  border: none;
  outline-color: black;
  margin: 15px;
}
button:hover {
    text-decoration: underline;
}
:disabled {
  background: #dddddd;
}
.pagenum {
  text-decoration: underline
}
</style>