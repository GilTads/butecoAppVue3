<template>
  <q-layout view="lHh lpR fFf">
    <div class="container">
      <q-header reveal :reveal-offset="30" style="backgroundColor: transparent">
        <q-toolbar class="text-accent">
          <q-btn
            size="25px"
            flat
            dense
            icon="menu"
            aria-label="Menu"
            @click="drawerLeft = !drawerLeft"
          />
          <q-space />
          <div class="text-h4 title">ButecoApp</div>
        </q-toolbar>
      </q-header>
      <q-drawer
        side="left"
        show-if-above
        v-model="drawerLeft"
        bordered
        :width="260"
        :breakpoint="500"
        content-style="background-color: #EAF1FF"
      >
        <q-scroll-area
          style="height: calc(100% - 150px);
          margin-top: 150px;
          border-right: 1px solid #8AB1F9"
        >
          <div class="q-pa-md">
            <q-list padding class="side-menu-title q-gutter-y-sm">
              <SidebarLink v-for="item in sidebarLinks" :key="item.title" v-bind="item" />

              <SidebarExpandedLink
                v-for="expanded in expandedLinks"
                :key="expanded.title"
                v-bind="expanded"
              />
            </q-list>
          </div>
        </q-scroll-area>
        <q-img
          class="absolute-top"
          src="~assets/images/logo-transparent.png"
          style="height: 150px;
            background: url('images/bar.jpeg') no-repeat center center;"
        ></q-img>
      </q-drawer>

      <q-page-container>
        <transition
          appear
          enter-active-class="animated fadeIn"
          leave-active-class="animated fadeOut"
          mode="out-in"
        >
          <router-view />
        </transition>
      </q-page-container>

      <q-footer reveal elevated>
        <div class="q-pr-md title text-h6 absolute-bottom-right padding">
          <p>
            Usuário:
            <strong>Dolores</strong>
          </p>
        </div>
      </q-footer>
    </div>
  </q-layout>
</template>

<script lang="ts">
import SidebarExpandedLink from '../components/dashboard/SidebarExpandedLink.vue';
import SidebarLink from '../components/dashboard/SidebarLink.vue';

import { defineComponent, ref } from 'vue';

import add from '../assets/icons/add.svg';
import tableIcon from '../assets/icons/add_table.svg';
import orderIcon from '../assets/icons/order.svg';
import moneyIcon from '../assets/icons/money.svg';

const linkData = [
  {
    title: 'Mesas',
    icon: tableIcon,
    link: '/dinner_tables',
  },
  {
    title: 'Pedidos',
    icon: orderIcon,
  },
  {
    title: 'Movimento',
    icon: moneyIcon,
  },
];

const expandedData = [
  {
    title: 'Cadastros',
    icon: add,
  },
];

export default defineComponent({
  name: 'Dashboard',
  components: {
    SidebarExpandedLink,
    SidebarLink,
  },
  props: {
    title: {
      type: String,
    },

    icon: {
      type: String,
    },
    link: {
      type: String,
    },
  },

  setup() {
    const drawerLeft = ref(false);
    const sidebarLinks = ref(linkData);
    const expandedLinks = ref(expandedData);

    return {
      drawerLeft,
      sidebarLinks,
      expandedLinks,
    };
  },
});
</script>

<style lang="scss" scoped>
.q-layout {
  background: url('../assets/images/bg-dash.png') no-repeat center center fixed;
  background-size: cover;
  width: 100%;
  height: 100%;
}
</style>
