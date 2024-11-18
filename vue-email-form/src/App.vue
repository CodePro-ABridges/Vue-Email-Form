<template>
  <EmailForm />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import EmailForm from './components/EmailForm.vue'

export default defineComponent({
  name: 'App',
  components: {
    EmailForm
  }
})
</script>

