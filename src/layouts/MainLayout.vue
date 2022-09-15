<template>

  <q-layout view="hHr lpR fFf">

    <!-- header -->
    <q-header class="bg-pink-2 text-white q-py-lg">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>

          <q-icon name="public" to="/" clickable size="lg" />

          MonSA

        </q-toolbar-title>

        <q-btn dense flat round icon="menu" @click="toggleRightDrawer"  />

      </q-toolbar>
    </q-header>

    <q-header elevated class="bg-purple">
      <q-toolbar>
        <q-btn flat round dense icon="menu" class="q-mr-sm" @click="toggleLeftDrawer" />
        <q-space ></q-space>
        <q-btn flat round dense icon="search" class="q-mr-xs" />
        <q-btn flat round dense icon="group_add" />
      </q-toolbar>
      <q-toolbar inset class="bg-blue ">
        <q-toolbar-title>
          <span><strong>Quasar</strong> Framework</span>
        </q-toolbar-title>
        <q-btn dense flat round icon="menu" @click="toggleRightDrawer"  />
      </q-toolbar>
    </q-header>

    <!-- sidebar gauche -->
    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
      <!-- drawer content -->
    </q-drawer>

    <!-- sidebar droite -->
    <q-drawer v-model="rightDrawerOpen" side="right" behavior="mobile" bordered>
      <!-- drawer content -->
    </q-drawer>

    <!-- contenu au milieu -->
    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          <div>Title</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
  
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const leftDrawerOpen = ref(false)
    const rightDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },

      rightDrawerOpen,
      toggleRightDrawer () {
        rightDrawerOpen.value = !rightDrawerOpen.value
      }
    }
  }
}
</script>
