<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title> 以琳數位化 </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer :width="200" v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> 以琳和撒那 </q-item-label>
        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container class="q-pa-md">
      <router-view />
    </q-page-container>
  </q-layout>
</template>
ƒ
<script setup lang="ts">
import { ref } from 'vue';
import EssentialLink, {
  EssentialLinkProps,
} from 'components/EssentialLink.vue';

defineOptions({
  name: 'MainLayout',
});

const linksList: EssentialLinkProps[] = [
  {
    title: '總表',
    // caption: 'quasar.dev',
    icon: 'attach_money',
    link: '/salary',
  },
  {
    title: '車用結帳單',
    icon: 'drive_eta',
    link: '/orderer_checkout',
  },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
