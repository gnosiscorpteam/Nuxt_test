<template>
</template>

<script setup>
import { useRouter } from 'vue-router';
const router = useRouter();

onMounted(() => {
  router.push('/login');
});

</script>