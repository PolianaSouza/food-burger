
<template>
  <q-layout view="hhh lpR fff">
    <q-header class="text-white row" height-hint="98">
      <q-toolbar class="q-ma-md col-md-9 col-sm-5 col-lg-9">
        <q-toolbar-title>
          <q-avatar class="q-mr-md">
            <img src="../assets/logo.png">
          </q-avatar>
          <strong>FOOD</strong> Burger
        </q-toolbar-title>
      </q-toolbar>
      <q-tabs align="right" class="q-mr-sm" active-color="yellow-14">
        <q-route-tab to="/" label="Fazer Pedido" />
        <q-route-tab to="/pedidos" label="Pedidos" />
      </q-tabs>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer class="text-white flex flex-center" style="height: 80px">
      <q-toolbar >
        <q-toolbar-title class="row flex-center">
          <q-avatar class="q-mr-md">
            <img src="../assets/logo.png">
          </q-avatar>
          <div class="text-overline"> <strong>FOOD</strong> Burger &copy; 2022</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>

<style scoped>
  .teste{
    display: flex !important;
    flex-direction: column;
  }
  .q-header, .q-footer {
    background-color: #15171d;
  }
</style>
