<template>
  <q-expansion-item :content-inset-level="0.3">
    <template v-slot:header>
      <q-item-section avatar>
        <q-img :src="icon" />
      </q-item-section>

      <q-item-section>{{ title }}</q-item-section>
    </template>

    <q-item
      clickable
      v-ripple
      v-for="item in expandedItems"
      :key="item.title"
      v-bind="item"
      :to="item.link"
    >
      <q-item-section avatar>
        <q-img class="expanded-item" :src="item.icon" />
      </q-item-section>

      <q-item-section>{{ item.title }}</q-item-section>
    </q-item>
  </q-expansion-item>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

import tableIcon from '../../assets/icons/add_table.svg';
import foodIcon from '../../assets/icons/food.svg';
import addPersonIcon from '../../assets/icons/add_person.svg';

const expandedItemData = [
  {
    title: 'Item',
    icon: foodIcon,
  },
  {
    title: 'Mesa',
    icon: tableIcon,
    link: '/table',
  },
  {
    title: 'Usuário',
    icon: addPersonIcon,
    link: '/users',
  },
];

export default defineComponent({
  name: 'SidebarExpandedLink',
  props: {
    icon: {
      type: String,
      required: true,
    },

    title: {
      type: String,
      required: true,
    },
  },
  setup() {
    const expandedItems = ref(expandedItemData);

    return { expandedItems };
  },
});
</script>

<style lang="scss">
.expanded-item {
  height: 28px;
  width: 28px;
}
</style>
