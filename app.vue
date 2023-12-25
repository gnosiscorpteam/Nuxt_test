<template>
    <div>
      <NuxtPage />
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