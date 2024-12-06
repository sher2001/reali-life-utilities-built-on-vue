<script setup>
import { computed, ref } from 'vue'

const formData = ref({
  firstName: '',
  lastName: '',
  email: '',
  password: '',
})

const submitted = ref(false)

const isValidEntry = (name) => name.trim() !== ''

const isFirstNameValid = computed(() => isValidEntry(formData.value.firstName))
const isLastNameValid = computed(() => isValidEntry(formData.value.lastName))
const isEmailValid = computed(() => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.value.email))
const isPasswordValid = computed(
  () => isValidEntry(formData.value.password) && formData.value.password.length >= 8,
)
const isFormValid = computed(
  () =>
    isFirstNameValid.value && isLastNameValid.value && isEmailValid.value && isPasswordValid.value,
)
const submitForm = () => {
  if (isFormValid.value) {
    submitted.value = true
  } else {
    console.log('Form is invalid. Please check the fields.')
  }
}

const generatePassword = () => {
  if (document.getElementById('password').type == 'password') {
    document.getElementById('password').type = 'text'
  }
  formData.value.password =
    'ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst0123456789!@#$%^&*()_+.,|=-;<>?:[]{}'
      .split('')
      .sort(() => {
        return 0.5 - Math.random()
      })
      .slice(0, 15)
      .join('')
}

const reSubmit = () => (submitted.value = false)
</script>

<template>
  <div class="pt-10 w-full h-auto max-h-screen flex-center gap-4 justify-between">
    <div class="w-full flex-center">
      <form @submit.prevent class="w-full md:w-3/4 lg:w-1/2 bg-gray-700 text-white rounded-3xl">
        <!-- from groups -->
        <div class="w-full flex-center flex-col gap-4 p-10">
          <!-- name group -->
          <div class="w-full flex flex-col md:flex-row gap-4">
            <!-- first name -->
            <div class="w-full flex flex-col gap-2">
              <label for="first-name">First Name</label>
              <input
                :disabled="submitted"
                v-model="formData.firstName"
                type="text"
                name="first-name"
                id="first-name"
                class="ui-button disabled-field"
              />
              <span v-if="!isFirstNameValid" class="text-pink-600 font-bold text-sm"
                >Invalid first name</span
              >
            </div>

            <!-- last name -->
            <div class="w-full flex flex-col gap-2">
              <label for="last-name">Last Name</label>
              <input
                :disabled="submitted"
                v-model="formData.lastName"
                type="text"
                name="last-name"
                id="last-name"
                class="ui-button disabled-field"
              />
              <span v-if="!isLastNameValid" class="text-pink-600 font-bold text-sm"
                >Invalid last name</span
              >
            </div>
          </div>

          <!-- mail group -->
          <div class="w-full flex flex-col gap-2">
            <label for="email">Email</label>
            <input
              :disabled="submitted"
              v-model="formData.email"
              type="email"
              name="email"
              id="email"
              class="ui-button disabled-field"
            />
            <span v-if="!isEmailValid" class="text-pink-600 font-bold text-sm"
              >Invalid last name</span
            >
          </div>

          <!-- enter password -->
          <div class="w-full flex flex-col gap-1">
            <div class="flex justify-between mr-1">
              <label for="password">Password</label>
              <!-- generate password -->
              <div class="w-fit">
                <button
                  :disabled="submitted"
                  @click="generatePassword"
                  class="ui-button p-1 disabled-field"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke-width="1.5"
                    stroke="currentColor"
                    class="size-6"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      d="M9.813 15.904 9 18.75l-.813-2.846a4.5 4.5 0 0 0-3.09-3.09L2.25 12l2.846-.813a4.5 4.5 0 0 0 3.09-3.09L9 5.25l.813 2.846a4.5 4.5 0 0 0 3.09 3.09L15.75 12l-2.846.813a4.5 4.5 0 0 0-3.09 3.09ZM18.259 8.715 18 9.75l-.259-1.035a3.375 3.375 0 0 0-2.455-2.456L14.25 6l1.036-.259a3.375 3.375 0 0 0 2.455-2.456L18 2.25l.259 1.035a3.375 3.375 0 0 0 2.456 2.456L21.75 6l-1.035.259a3.375 3.375 0 0 0-2.456 2.456ZM16.894 20.567 16.5 21.75l-.394-1.183a2.25 2.25 0 0 0-1.423-1.423L13.5 18.75l1.183-.394a2.25 2.25 0 0 0 1.423-1.423l.394-1.183.394 1.183a2.25 2.25 0 0 0 1.423 1.423l1.183.394-1.183.394a2.25 2.25 0 0 0-1.423 1.423Z"
                    />
                  </svg>
                </button>
              </div>
            </div>
            <input
              :disabled="submitted"
              v-model="formData.password"
              type="password"
              name="password"
              id="password"
              class="ui-button disabled-field"
            />
            <span v-if="!isPasswordValid" class="text-pink-600 font-bold text-sm"
              >Invalid last name</span
            >
          </div>

          <!-- submit button -->
          <div class="mt-4 w-full md:w-1/4">
            <button
              :disabled="!isFormValid || submitted"
              type="submit"
              @click="submitForm"
              class="disabled-field w-full ui-button px-2 py-3"
            >
              Submit
            </button>
          </div>
          <div class="mt-4 w-full md:w-1/4">
            <button
              v-if="submitted"
              @click="reSubmit"
              class="disabled-field w-full ui-button px-2 py-3"
            >
              Re-Submit
            </button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>
