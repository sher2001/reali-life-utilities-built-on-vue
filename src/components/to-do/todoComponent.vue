<script setup>
import { ref } from 'vue'

let tasks = ref([])
let newTask = ref('')

const addTask = () => {
  if (newTask.value.trim() != '') {
    tasks.value.push(newTask.value)
    newTask.value = ''
  }
}

const removeTask = (index) => tasks.value.splice(index, 1)
</script>
<template>
  <div class="w-full h-auto max-h-screen flex-center gap-4 justify-between">
    <div class="w-full lg:w-1/2 flex-center flex-col gap-2">
      <!-- add task bar -->
      <div class="w-full flex-center gap-2">
        <input
          v-model="newTask"
          @keyup.enter="addTask"
          type="text"
          class="size-10 w-full ui-button focus:ring-0 focus:border-none focus:shadow-md focus:shadow-indigo-800"
          autofocus
          placeholder="add your task title here and press enter"
        />
        <div @click="addTask" class="size-8 ui-button text-indigo-500">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="size-5"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M13.5 4.5 21 12m0 0-7.5 7.5M21 12H3"
            />
          </svg>
        </div>
      </div>
      <!-- tasks list -->
      <div class="w-full mt-3 pr-2 fixed-max-height rounded-md grid md:grid-cols-2 gap-4">
        <!-- evrything should repeat here -->
        <div class="w-full ui-button" v-for="(task, i) in tasks" :key="i">
          <div class="w-full p-5 h-auto mt-2 flex items-center justify-between">
            <span class="max-w-lg overflow-hidden">{{ task }}</span>
            <div @click="removeTask(i)" class="px-3 text-red-500 cursor-pointer">
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
                  d="m14.74 9-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 0 1-2.244 2.077H8.084a2.25 2.25 0 0 1-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 0 0-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 0 1 3.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 0 0-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 0 0-7.5 0"
                />
              </svg>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
