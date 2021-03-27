<template>
  <q-item clickable v-ripple :to="link">
    <q-item-section avatar>
      <q-img :src="icon" />
    </q-item-section>

    <q-item-section>{{ title }}</q-item-section>
  </q-item>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'SidebarLink',
  props: {
    icon: {
      type: String,
      required: true,
    },

    title: {
      type: String,
      required: true,
      default: '',
    },

    link: {
      type: String,
    },
  },
});
</script>
