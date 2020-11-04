<template>
  <div id="app">
    <HeaderTop
      v-on:search-value="searchInput($event)"
    />
    {{searchValue}}

    <SideNavBar
      v-on:random-color="expandColor($event)"
    />
    <ColorView  
      v-bind:cssColorData="cssColorData" 
      v-bind:size="size"
      v-on:send-color="expandColor($event)"
    />
    <DetailView
      v-if="colorToExpand.length ===  1"
      v-bind:colorToExpand="colorToExpand"
      v-on:clear-color="clearColor()"
    />


  </div>
</template>

<script>
  //import { slackData } from './assets/slackData'
  import HeaderTop from '@/components/HeaderTop.vue'
  import SideNavBar from '@/components/SideNavBar.vue'
  import ColorView from '@/components/ColorView.vue'
  import DetailView from '@/components/DetailView.vue'
  import { cssData } from './assets/cssData'

  export default {
    name: 'app',
    components: {
      HeaderTop,
      SideNavBar,
      ColorView,
      DetailView,
   
    },
    data() {
      return {
        searchValue: '',
        cssColorData: [ ...cssData.red, ...cssData.orange, ...cssData.yellow, ...cssData.green, ...cssData.blue, ...cssData.purple, ...cssData.brown, ...cssData.gray], 
        colorId: '',
        colorToExpand: [],
        size: 12,
      }
    },
    methods: {
      searchInput(searchString) {
        this.searchValue = searchString
        //console.log(this.searchValue)
        this.colorToExpand = this.cssColorData.filter(
          color => color.HexCode === searchString
        )
        //console.log(this.colorToExpand)
        },
      expandColor(colorIdPassed) {
        this.colorId = colorIdPassed
        //console.log(this.colorId)
        this.colorToExpand = this.cssColorData.filter(
          color => color.id === colorIdPassed
        )
        //console.log(this.colorToExpand)
      },
      clearColor() {
        this.colorToExpand = []

      },
    },
  }

</script>

<style>
button {
  background: #38d8a3;
  border: 1px solid #38d8a3;
  margin: 2px;
  font-family: "Times New Roman", Times, serif;
}
button:hover {
  background-color: rgb(77, 82, 78); 
  border: 1px solid rgb(77, 82, 78);
}
.error-message {
    color: #d33c40;
  }
  
</style>
