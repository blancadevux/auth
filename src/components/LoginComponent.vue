<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h2 class="mt-4">Inicio de sesión</h2>
        <form>
          <div class="mb-3">
            <label for="exampleInputEmail1" class="form-label">Correo</label>
            <input
              id="exampleInputEmail1"
              type="email"
              class="form-control"
              v-model="email"
            />
          </div>
          <div class="mb-3">
            <label for="exampleInputPassword1" class="form-label"
              >Contraseña</label
            >
            <input
              id="exampleInputPassword1"
              type="password"
              class="form-control"
              v-model="password"
            />
          </div>
          <button @click="signIn" class="btn btn-primary">Ingresar</button>
        </form>
      </div>
    </div>
    <div v-if="ok !== null" class="row mt-4">
      <div class="col-12">
        <div
          v-if="ok"
          class="alert alert-success"
          role="alert"
          style="width: 28rem"
        >
          Inicio de sesión correcto.
        </div>
        <div
          v-else
          class="alert alert-danger"
          role="alert"
          style="width: 28rem"
        >
          Hubo un error. Intente más tarde.
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { signInWithEmailAndPassword, getAuth } from '../auth';

export default {
  data() {
    return {
      email: '',
      password: '',
      ok: null,
    };
  },
  methods: {
    async signIn() {
      try {
        const { email, password } = this;
        const auth = getAuth();
        const user = await signInWithEmailAndPassword(auth, email, password);
        console.log(user);
        this.ok = true;
      } catch (error) {
        console.log(error);
        this.ok = false;
      }
    },
  },
};
</script>

<style scoped>
form {
  width: 28rem;
}
</style>
