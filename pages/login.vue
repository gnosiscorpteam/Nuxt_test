<template>
  <div class="vh-100 d-flex justify-content-center align-items-center login-background">
    <div class="p-5 mb-5 ml-5" style="max-width: 400px; width: 100%; border-left: 1px solid white;">
      <h2 class="mb-4 text-left text-white">Sign In</h2>
      <form @submit.prevent="login">
        <div class="mb-3">
          <input type="text" class="form-control" id="email" placeholder="Email address" required
            v-model="credentials.email" />
        </div>
        <div class="mb-3">
          <input type="password" class="form-control" id="password" placeholder="Password" required
            v-model="credentials.password" />
        </div>
        <div class="mb-4 form-check">
          <input type="checkbox" class="form-check-input" id="rememberMe" v-model="credentials.rememberMe" />
          <label class="form-check-label text-white" for="rememberMe">Remember me</label>
        </div>
        <div class="row">
          <button type="submit" class="btn btn-warning mx-2 col-4 text-white">Submit</button>
          <button type="submit" class="btn btn-info col-6 mx-2 text-white">Single-Sign On</button>
        </div>
        <p class="mt-3 text-left">
          <a href="#" class="text-white">Forgotten password?</a>
        </p>
      </form>
    </div>
  </div>
</template>


<script setup>
import { ref } from 'vue';

const credentials = ref({
  email: '',
  password: '',
  rememberMe: false
});

const login = () => {
  console.log('Logging in with:', credentials.value);
  if (credentials.value.email == 'admin' && credentials.value.password == 'admin')
    useRouter().push('/homepage');
};
</script>

<style scoped>
.login-background {
  background-color: #21689A;
}
</style>