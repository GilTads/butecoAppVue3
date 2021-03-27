<template>
  <div class="container">
    <div class="content">
      <div class="row justify-center">
        <div class="col">
          <q-img
            src="../assets/images/logo-transparent.png"
            alt=""
            style="max-width: 450px; max-height: 230px;"
          />
        </div>
      </div>

      <q-form class="q-gutter-md" @submit="onSubmit">
        <h2 class="main-font text-center text-h2">ButecoApp</h2>
        <q-input
          rounded
          outlined
          color="#518AF6"
          bg-color="secondary"
          label="Usuário"
          class="input-text"
        >
          <template v-slot:append>
            <q-icon name="person" />
          </template>
        </q-input>
        <q-input
          rounded
          outlined
          type="password"
          color="#518AF6"
          bg-color="secondary"
          label="Senha"
          class="input-text"
        >
          <template v-slot:append>
            <q-icon name="lock" />
          </template>
        </q-input>
        <div class="row justify-end">
          <q-btn
            type="submit"
            size="lg"
            rounded
            label="ENTRAR"
            color="accent"
            class="login"
            :loading="submitting"
          >
            <template v-slot:loading>
              <q-spinner-facebook />
            </template>
          </q-btn>
        </div>
      </q-form>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'Signin',

  setup() {
    const submitting = ref(false);

    function onSubmit() {
      submitting.value = true;

      setTimeout(() => {
        submitting.value = false;
      }, 3000);

      return submitting;
    }

    return { submitting, onSubmit };
  },
});
</script>

<style lang="scss" scoped>
.container {
  background: url('../assets/images/login-background-min.png') no-repeat center
    center fixed;
  display: flex;
  flex-direction: column;

  place-content: center;
  background-size: cover;

  align-items: center;
  width: 100%;
  height: 100vh;
}
.content {
  img {
    max-width: 450px;
    max-height: 230px;
  }
  .login {
    width: 180px;
    height: 50px;
  }
}
</style>
