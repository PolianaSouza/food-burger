<template>
  <q-page >
    <Banner/> 
    <p class="text-h3 text-center q-mt-md" >Monte o seu burger:</p>
    <burger-form/>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import Banner from '../components/Banner.vue'
import BurgerForm from '../components/BurgerForm.vue'

export default defineComponent({
  name: 'IndexPage',
  components: {
    Banner,
    BurgerForm,
  }
})
</script>

<style scoped>
  
</style>

