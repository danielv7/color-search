<template>
 <div class="colorview">
   <!--
  <table class="table table-bordered">
    <thead>
      <tr>
        <th>Color Name</th>
        <th>Color Code</th>
      </tr>
    </thead>
    <tbody>
    <tr v-for="color in cssColorData" :key="color.id">
      <td>{{ color.color }}</td>
      <td>{{ color.HexCode }}</td>
    </tr>
    </tbody>
  </table>
  -->
<!--
    <section class="flex-container" >
      <div v-for="color in cssColorData" :key="color.id + Math.random()" class="colorbox" v-bind:style="{ backgroundColor: color.HexCode}">
        {{ color.color }} 
        {{ color.HexCode }} 
      </div>
    </section>
    -->

<!--
    <section class="flex-container">
      <button v-for="color in cssColorData" :key="color.id" class="card" v-bind:style="{ backgroundColor: color.HexCode}">
        <div class="container">
          {{ color.HexCode }} 
        </div>
      </button>
    </section>
    -->
    <section class="flex-container">
      <button v-for="color in cssColorData" :key="color.id"  class="card" @click="handleClick(color.id)" v-bind:style="{ backgroundColor: color.HexCode}">
        <div class="container">
          {{ color.HexCode }} 
        </div>
      </button>
    </section>

		<ul class="vertical-center">
				<button type="button" class="page-link" v-if="page != 1" @click="page--"> Previous </button>
				<button type="button" class="page-link" v-for="(pageNumber,index) in pages.slice(page-1, page+5)" :key="index" @click="page = pageNumber"> {{pageNumber}} </button>
				<button type="button" @click="page++" v-if="page < pages.length" class="page-link"> Next </button>
		</ul>	

 
  </div>


</template>

<script>
  export default {
  name: 'colorview',
  props: {
    cssColorData: Array,
  },
  data () {
		return {
			posts : [],
			page: 1,
			perPage: 12,
      pages: [],
		}
  },
  methods:{
		getPosts () {	
      this.posts = this.cssColorData
		},
		setPages () {
			let numberOfPages = Math.ceil(this.posts.length / this.perPage);
			for (let index = 1; index <= numberOfPages; index++) {
				this.pages.push(index);
			}
		},
		paginate (posts) {
			let page = this.page;
			let perPage = this.perPage;
			let from = (page * perPage) - perPage;
			let to = (page * perPage);
			return  posts.slice(from, to);
    },
    handleClick (colorId) {
      this.$emit('send-color', colorId)
    }
	},
	computed: {
		cssColorData () {
			return this.paginate(this.posts);
		}
	},
	watch: {
		posts () {
      this.setPages();
		}
	},
	created(){
		this.getPosts();
	},
	filters: {
		trimWords(value){
			return value.split(" ").splice(0,20).join(" ") + '...';
		}
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

button.page-link {
    display: inline-block;
    font-size: 15px;
    color: black;
    font-weight:50;
    background-color: white; 
    border: none;
    outline-color: black;
    margin: 1px;
}
button:hover {
    text-decoration: underline;
}

.flex-container {
  display: flex;
  flex-wrap: wrap;
}

.card {
  /* 
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  */
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
/*
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
  width: 1000px;
  height: 600px;
  border-radius:1%;
  position: absolute, top 20px, left 20px;

}
*/

</style>