<template>
  <header>
      <h1>
        <img src="../assets/logo.png" alt="">  
      </h1>
      <button class="button" @click="alterTheme">
        {{ textButton }}
      </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'BarraLateral',
  emits:['toThemeChanged'],
  data(){
    return {
      darkModeActived: false
    }
  },
  computed:{
    textButton(){
      if(this.darkModeActived){
        return 'Disable dark mode'
      }
      return 'Enable dark mode'
    },
  },
  methods:{
    alterTheme(){
      this.darkModeActived = !this.darkModeActived
      this.$emit('toThemeChanged', this.darkModeActived)
    }
  }
})
</script>

<style scoped>
header {
  text-align: center;
  padding: 0rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 1.5rem;
    height: auto;
  }
}
</style>