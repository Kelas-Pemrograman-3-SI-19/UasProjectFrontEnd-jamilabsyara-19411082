<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="bg-white text-blue-grey-14">
      <q-toolbar>
        <q-btn dense flat round @click="leftDrawerOpen = !leftDrawerOpen" icon="menu"/>
        <q-space></q-space>
        <q-btn flat round>
          <q-avatar>
            <img src="https://t3.ftcdn.net/jpg/03/65/06/44/360_F_365064449_riVvZFG0iXMPsa2ZcqlcfUiBBFG1nuuU.jpg">
          </q-avatar>
           <q-menu>
          <q-list style="min-width: 100px">
            <q-item clickable v-close-popup>
              <q-item-section>Profile</q-item-section>
            </q-item>
            <q-item clickable v-close-popup @click="logout()">
              <q-item-section>Logout</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
        </q-btn>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      class="text-white bg-black"
    >
    <q-scroll-area class="fit">
      <q-list separator>
        <q-item  class="justify-center text-center q-mb-md q-mt-md">
          <div>
              <q-avatar size="75px">
                <img src="https://t3.ftcdn.net/jpg/03/65/06/44/360_F_365064449_riVvZFG0iXMPsa2ZcqlcfUiBBFG1nuuU.jpg">
              </q-avatar>
          <div class="text-weight-bold q-mt-md">{{ $q.localStorage.getItem('dataUser').namalengkap }}</div>
          <div>GAME STRORE APP</div>
          </div>
        </q-item>

        <q-item clickable active-class="active" v-ripple exact :to="{ name: 'DashboardAdmin' }">
          <q-item-section avatar>
            <q-icon name="dashboard"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Dashboard</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable active-class="active" v-ripple exact :to="{ name: 'dataGAME' }">
          <q-item-section avatar>
            <q-icon name="dashboard"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Data Game</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable active-class="active" v-ripple exact :to="{ name: 'inputBarang' }">
          <q-item-section avatar>
            <q-icon name="input"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Input Game</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable active-class="active" v-ripple exact :to="{ name: 'dataUser' }">
          <q-item-section avatar>
            <q-icon name="supervisor_account"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Data User</q-item-label>
          </q-item-section>
        </q-item>

      </q-list>
    </q-scroll-area>
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
        </q-item-label>

      </q-list>
    </q-drawer>

    <q-page-container class="bg-grey-1">
      <router-view />
    </q-page-container>
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
  },
  methods: {
    logout () {
      this.$q.localStorage.remove()
      this.$router.push({ name: 'loginPage' })
    }
  }
})
</script>
<style scoped>
.active {
  color: black;
  background-color: #fafafa;
  padding-right: 10px;
}
</style>
