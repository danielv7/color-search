<template>
  <div class="sidenavbar">
    <button class="btn" @click="handleClick()">Random Color</button>
    <button>Red</button>
    <button>Orange</button>
    <button>Yellow</button>
    <button>Green</button>
    <button>Blue</button>
    <button>Purple</button>
    <button>Brown</button>
    <button>Gray</button>
     <button></button>
  </div>
</template>

<script>
  export default {
  name: 'side-nav-bar',
  methods:{
		handleClick () {	
      this.randomColorNum  = String(Math.floor(Math.random() * 103) + 1)
      this.$emit('random-color', this.randomColorNum)
    },
  },
 
}
</script>

<style scoped>

.sidenavbar {
  height: 95%; /* Full-height: remove this if you want "auto" height */
  width: 270px; /* Set the width of the sidebar */
  position: fixed; /* Fixed Sidebar (stay in place on scroll) */
  z-index: 1; /* Stay on top */
  top: 90px; /* Stay at the top */
  left: 0;
  background-color: #D3D3D3; /* Black */
  overflow-x: hidden; /* Disable horizontal scroll */
  padding-top: 20px;

}
.sidenavbar button {
  padding: 8px 8px 6px 16px;
  text-decoration: none;
  font-size: 22px;
  color: #484848;
  display: block;
}
.sidenavbar button:hover {
  color: #f1f1f1;
}
.btn {
  border: 1px solid black;
  background-color: white;
  color: black;
  padding: 28px 28px;
  font-size: 8px;
  cursor: pointer;
  border-radius: 10px;
  outline-color: black;
  margin-left: 10px;
}
.btn:hover {
  background-color: rgb(46, 46, 40);
}
button {
  background: #D3D3D3;
  border: 1px solid #D3D3D3;
  margin: 5px;
  outline-color: black;
}

</style>