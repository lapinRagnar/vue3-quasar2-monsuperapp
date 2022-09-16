<template>

  <q-layout view="hHh lpR fFf">

    <!-- header -->
    <q-header elevated class="bg-purple">

      <q-toolbar>
        <q-btn flat round dense icon="menu" class="q-mr-sm" @click="toggleLeftDrawer" />
        <q-space ></q-space>

        <q-avatar size="lg" class="q-mr-sm">
          <q-badge floating color="red">2</q-badge>
          <q-btn flat round dense icon="notifications" class="q-mr-sm" />
        </q-avatar>

        <q-avatar size="lg">
          <img src="https://cdn.quasar.dev/img/avatar.png">
        </q-avatar>

        <q-btn-dropdown
          fab-mini
          class="monDropdown"
          flat
          unelevated

          size="lg"
        >
          <q-list class="largeur_list" padding>
            <q-item clickable v-close-popup @click="onItemClick" v-ripple >
              <q-item-section avatar >
                <q-icon name="settings"/>
              </q-item-section>
              <q-item-section>
                <q-item-label>parametres</q-item-label>
              </q-item-section>
            </q-item>

            <q-item clickable v-close-popup @click="onItemClick" v-ripple>
              <q-item-section avatar >
                <q-icon name="post_add"/>
              </q-item-section>
              <q-item-section>
                <q-item-label>articles</q-item-label>
              </q-item-section>
            </q-item>



            <q-item clickable v-ripple @click="onItemClick">
              <q-item-section avatar>
                <q-icon name="send" />
              </q-item-section>

              <q-item-section>
                Send
              </q-item-section>
            </q-item>


            <q-item clickable v-ripple @click="onItemClick">
              <q-item-section avatar>
                <q-icon name="drafts" />
              </q-item-section>

              <q-item-section>
                Drafts
              </q-item-section>
            </q-item>


            <q-item clickable v-close-popup @click="onItemClick">
              <q-item-section avatar >
                <q-icon name="power_settings_new"/>
              </q-item-section>
              <q-item-section>
                <q-item-label>se deconnecter</q-item-label>
              </q-item-section>
            </q-item>


          </q-list>

        </q-btn-dropdown>

      </q-toolbar>

      <q-toolbar inset class="bg-blue ">
        <q-toolbar-title>
          Mon <strong>Super</strong> App
        </q-toolbar-title>

        <q-input
          rounded
          borderless
          v-model="text"
          label="qu'est ce que tu veux..."
          label-color="orange"
          color="red"
          dark
          input-style="width: 200px;"
        >
          <q-btn flat round dense icon="search" class="q-mr-xs"  />
        </q-input>

        <q-space />

        <q-btn dense flat round icon="menu" @click="toggleRightDrawer" />

      </q-toolbar>
    </q-header>

    <!-- sidebar gauche -->
    <q-drawer
      show-if-above
      v-model="leftDrawerOpen"
      side="left"
      bordered
      :mini="miniState"
      @mouseover="miniState = false"
      @mouseout="miniState = true"
      :width="150"

    >
      <!-- drawer content -->
      <q-list padding>
        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="inbox" />
          </q-item-section>

          <q-item-section>
            Inbox
          </q-item-section>
        </q-item>

        <q-item active clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="star" />
          </q-item-section>

          <q-item-section>
            Star
          </q-item-section>
        </q-item>

        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="send" />
          </q-item-section>

          <q-item-section>
            Send
          </q-item-section>
        </q-item>

        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="drafts" />
          </q-item-section>

          <q-item-section>
            Drafts
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <!-- sidebar droite -->
    <q-drawer
      v-model="rightDrawerOpen"
      side="right"
      behavior="desktop"
      bordered
      show-if-above
    >
      <!-- drawer content -->
    </q-drawer>

    <!-- contenu au milieu -->
    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- <q-footer class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          <div>Title</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer> -->

  </q-layout>

</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const leftDrawerOpen = ref(false)
    const rightDrawerOpen = ref(false)

    const miniState = ref(true)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },

      rightDrawerOpen,
      toggleRightDrawer () {
        rightDrawerOpen.value = !rightDrawerOpen.value
      },

      miniState,

      onMainClick () {
        // console.log('Clicked on main button')
      },

      onItemClick () {
        // console.log('Clicked on an Item')
      }
    }
  }
}
</script>

<style lang="sass" scoped>
  .monDropdown
    position: absolute
    right: 10px
    top: 19px

  .largeur_list
    width: 200px

</style>
