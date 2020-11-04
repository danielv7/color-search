<template>
  <nav>
    <img :src="mySVGLogo"/>
    <div>
        <form @submit.prevent="handleSubmit">
            <input v-model="searchInput" type="text" placeholder="Search"/>
        </form>
    </div>
  </nav>
</template>

<script>
  export default {
  name: 'headertop',
  data(){
    return {
      mySVGLogo: require('@/assets/logo-symbol.svg'),
      searchInput: '',
    }
  },
  methods: {
      handleSubmit() {
        if (this.searchInput) {
          this.$emit('search-value', this.searchInput)
          }
          this.searchInput = '';
        }, 
    },
 
}
</script>

<style scoped>
nav {
  background:#303030;
  height: 90px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-right: 3%;
  padding-left: 3%;
}
input {
    background-color: white;
    width: 250px;
  }
</style>