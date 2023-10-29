<script setup>
import { ref, defineProps, onMounted } from 'vue'
import NewsletterView from './views/NewsletterView.vue';
import SubmittedView from './views/SubmittedView.vue';

const submittedEmail = ref('');

const operation = (email) => {
  submittedEmail.value = email;
  console.log(`submitted email is ${submittedEmail.value}`)
}

</script>

<template>
  <NewsletterView v-if="submittedEmail == ''" @emailInput="(email) => operation(email)" />
  <SubmittedView v-else :email="submittedEmail"/>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
</style>