<template>
  <div class="q-pa-md q-mt-none">
    <div>
      <q-toolbar class="text-accent">
        <q-avatar size="100px" icon="img:icons/dinner-table.png" />
        <q-toolbar-title>
          <div class=" page-title">Mesas</div>
        </q-toolbar-title>
      </q-toolbar>
    </div>
    <div class="q-pa-sm row q-gutter-lg q-ml-sm">
      <div
        class=" col-md-2 col-sm-4"
        v-for="table in dinnerTable"
        :key="table.tableNumber"
      >
        <q-card
          class="dinner-table"
          :style="`backgroundColor: ${table.color}; cursor: pointer`"
        >
          <q-card-section>
            <div class="row justify-center">
              <div class="text-h5">Fulano</div>
            </div>
            <q-separator spaced inset vertical />
            <div class="row justify-center">
              <div class="text-h2">{{ table.tableNumber }}</div>
            </div>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';

const dinnerTableData = [
  {
    color: '#FF526F',
    tableNumber: 1,
  },
  {
    color: '#E3E4E4',
    tableNumber: 2,
  },
  {
    color: '#E3E4E4',
    tableNumber: 3,
  },
  {
    color: '#E3E4E4',
    tableNumber: 4,
  },
  {
    color: '#FF526F',
    tableNumber: 5,
  },
  {
    color: '#E3E4E4',
    tableNumber: 6,
  },
  {
    color: '#E3E4E4',
    tableNumber: 7,
  },
  {
    color: '#FF526F',
    tableNumber: 8,
  },
  {
    color: '#E3E4E4',
    tableNumber: 9,
  },
  {
    color: '#E3E4E4',
    tableNumber: 10,
  },
  {
    color: '#E3E4E4',
    tableNumber: 11,
  },
  {
    color: '#E3E4E4',
    tableNumber: 12,
  },
  {
    color: '#E3E4E4',
    tableNumber: 13,
  },
  {
    color: '#E3E4E4',
    tableNumber: 14,
  },
  {
    color: '#E3E4E4',
    tableNumber: 15,
  },
  {
    color: '#E3E4E4',
    tableNumber: 16,
  },
];

export default defineComponent({
  setup() {
    const dinnerTable = reactive(dinnerTableData);
    return { dinnerTable };
  },
});
</script>

<style lang="scss" scoped>
.dinner-table {
  margin-left: 20px;
  width: 100%;
  max-width: 150px;
  height: 150px;
  transition: 0.2s;

  &:hover {
    opacity: 0.8;
  }
}
</style>
