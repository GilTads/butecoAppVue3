<template>
  <div class="q-pa-md q-mt-none">
    <div>
      <q-toolbar class="text-accent">
        <q-avatar size="80px" icon="people" />
        <q-toolbar-title>
          <div class="page-title">Usuários</div>
        </q-toolbar-title>
        <q-btn flat round dense size="24px" icon="person_add" @click="open = true">
          <q-tooltip content-style="background-color: #32054E">Novo Usuário</q-tooltip>
        </q-btn>
      </q-toolbar>
    </div>
    <q-table
      color="primary"
      card-class="bg-cyan-1"
      :dense="$q.screen.lt.md"
      title="Usuários"
      :data="data"
      :columns="columns"
      :filter="filter"
      :loading="loading"
      row-key="name"
      separator="horizontal"
    >
      <template v-slot:top-right>
        <q-input outlined dense debounce="300" v-model="filter" placeholder="Procurar">
          <template v-slot:append>
            <q-icon name="search" />
          </template>
        </q-input>
      </template>

      <template v-slot:body-cell-info="props">
        <q-td :props="props">
          <div class="info">
            <q-btn flat round size="16px">
              <q-icon name="edit" style="cursor: pointer" />
            </q-btn>
          </div>
        </q-td>
      </template>
    </q-table>

    <q-dialog v-model="open" persistent transition-show="flip-down" transition-hide="flip-up">
      <q-card class="bg-white text-primary">
        <q-toolbar>
          <q-avatar>
            <q-icon name="person_add" color="accent" size="32px"></q-icon>
          </q-avatar>
          <q-space />
          <div class="title text-h5 q-mr-md">Cadastro de Usuário</div>

          <q-btn flat round dense icon="close" v-close-popup />
        </q-toolbar>

        <q-card-section class="q-pt-xl">
          <q-form class="q-gutter-md" style="width: 500px">
            <q-input
              class="input-text"
              rounded
              outlined
              color="#518AF6"
              bg-color="secondary"
              v-model="name"
              label="Nome de usuário *"
              lazy-rules
              :rules="[val => (val && val.length > 0) || 'Insira o nome']"
            />

            <q-input
              class="input-text"
              rounded
              outlined
              color="#518AF6"
              bg-color="secondary"
              type="password"
              v-model="password"
              label="Senha *"
              lazy-rules
              :rules="[val => (val !== null && val !== '') || 'Insira a senha']"
            />

            <q-toggle v-model="accept" color="positive" label="Administrador" />

            <div class="row justify-end">
              <q-btn label="Limpar" type="reset" color="negative" />
              <q-btn label="Cadastrar" type="submit" color="positive" class="q-ml-sm" />
            </div>
          </q-form>
        </q-card-section>
      </q-card>
    </q-dialog>
  </div>
</template>
<script lang="ts">
import { defineComponent, reactive, ref } from 'vue';

export default defineComponent({
  setup() {
    const columns = reactive([
      {
        name: 'codigo',
        required: true,
        label: 'Código',
        align: 'left',
        field: (row: { code: string }) => row.code,
        format: (val: string) => `${val}`,
        sortable: true,
      },
      {
        name: 'name',
        align: 'center',
        label: 'Nome',
        field: 'name',
        sortable: true,
      },
      {
        name: 'type',
        label: 'Função',
        align: 'center',
        field: 'type',
        sortable: true,
      },
      {
        name: 'info',
        label: 'Info',
        field: 'info',
        align: 'center',
      },
    ]);

    const data = reactive([
      {
        code: 1,
        name: 'Dolores',
        type: 'Adm',
      },
      {
        code: 2,
        name: 'Adriano',
        type: 'Adm',
      },
      {
        code: 3,
        name: 'Geovane',
        type: 'Garçom',
      },
    ]);
    const filter = ref('');
    const loading = ref(false);
    const open = ref(false);
    const accept = ref(false);
    const name = ref('');
    const password = ref('');

    return {
      columns,
      data,
      filter,
      loading,
      open,
      accept,
      name,
      password,
    };
  },
});
</script>
<style lang="scss"></style>
