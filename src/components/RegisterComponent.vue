<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h2 class="mt-4">Registro</h2>
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
          <button @click="register" class="btn btn-primary">Registrar</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import { createUserWithEmailAndPassword, auth } from '../auth';

export default {
  data() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    async register() {
      try {
        const userCredential = await createUserWithEmailAndPassword(
          auth,
          this.email,
          this.password
        );
        const user = userCredential.user;
        console.log(user);
      } catch (error) {
        console.log(error);
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
