
<template>
  <div class="min-h-screen bg-gray-50 flex items-center justify-center">
    <div class="max-w-md w-full p-6 bg-white rounded-lg shadow-md">
      <h2 class="text-2xl font-bold mb-6 text-center text-gray-800">Sign Up</h2>

      <form @submit.prevent="onSubmit" class="space-y-4">
        <div>
          <label for="email" class="block text-sm font-medium text-gray-700">Email Address</label>
          <input
            id="email"
            type="email"
            v-model="email"
            @blur="touchField"
            class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:ring-blue-500 focus:border-blue-500 p-2 border"
            :class="{ 'border-red-500': isFieldInvalid }"
          />
          <!-- Error Messages -->
          <div v-if="isFieldInvalid" class="mt-1 text-sm text-red-500">
            <span v-if="!email">Email is required</span>
            <span v-else>Please enter a valid email address</span>
          </div>
        </div>

        <button
          type="submit"
          :disabled="!isValidEmail"
          :class="{
            'w-full p-2 rounded-md focus:outline-none focus:ring-2 focus:ring-offset-2 transition-colors text-white': true,
            'bg-blue-500 hover:bg-blue-600 focus:ring-blue-500': !isSubmitted,
            'bg-green-500 hover:bg-green-600 focus:ring-green-500': isSubmitted,
            'opacity-50 cursor-not-allowed': !isValidEmail
          }"
        >
          {{ submitButtonText }}
        </button>

        <!-- Reset Button -->
        <button
          v-if="isSubmitted"
          type="button"
          @click="resetForm"
          class="w-full mt-2 bg-gray-500 text-white p-2 rounded-md hover:bg-gray-600 focus:outline-none focus:ring-2 focus:ring-gray-500 focus:ring-offset-2 transition-colors"
        >
          Submit Another
        </button>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, computed } from 'vue'

export default defineComponent({
  name: 'EmailForm',
  setup() {
    // State
    const email = ref('')
    const touched = ref(false)
    const isSubmitted = ref(false)

    // Email validation using regex
    const isValidEmail = computed(() => {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
      return email.value && emailRegex.test(email.value)
    })

    // Computed properties
    const isFieldInvalid = computed(() => {
      return touched.value && !isValidEmail.value
    })

    const submitButtonText = computed(() => {
      if (isSubmitted.value) return 'Submitted Successfully!'
      return 'Submit'
    })

    // Methods
    const touchField = () => {
      touched.value = true
    }

    const onSubmit = async () => {
      if (isValidEmail.value) {
        // Simulate API call
        await new Promise(resolve => setTimeout(resolve, 500))

        console.log('Form submitted:', email.value)
        isSubmitted.value = true
      }
    }

    const resetForm = () => {
      email.value = ''
      touched.value = false
      isSubmitted.value = false
    }

    return {
      email,
      isValidEmail,
      isFieldInvalid,
      isSubmitted,
      submitButtonText,
      touchField,
      onSubmit,
      resetForm
    }
  }
})
</script>
