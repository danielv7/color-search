<template>
  <div class="sidenavbar">
    <button class="btn" @click="handleClick()">Random Color</button>
    <div class="colorlist">Red</div>
    <div class="colorlist">Orange</div>
    <div class="colorlist">Yellow</div>
    <div class="colorlist">Green</div>
    <div class="colorlist">Blue</div>
    <div class="colorlist">Purple</div>
    <div class="colorlist">Brown</div>
    <div class="colorlist">Gray</div>
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
  padding: 15px 30px 15px 30px;
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
  margin-bottom: 25px;
  margin-top: 20px;
  margin-left: 30px;
}
.btn:hover {
  background-color: rgb(46, 46, 40);
}
.colorlist {
  background: #D3D3D3;
  border: 1px solid #D3D3D3;
  padding-left: 16px;
  margin: 5px;
  outline-color: black;
  font-size: 22px;
  font-weight: 550;
  font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;


}

</style>