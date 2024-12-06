<script setup>
import { ref } from 'vue'

const display = ref('0')

const calculate = () => {
  display.value = eval(display.value).toString()
}

const clicked = (val) => {
  if (display.value === '0') {
    display.value = ''
  }
  display.value = display.value.concat(val)
}

const clearDisplay = () => {
  display.value = '0'
}

const backSpace = () => {
  if (display.value.at(-1) === ' ') {
    display.value = display.value.slice(0, -1)
  }
  display.value = display.value.slice(0, -1)
}

const toggleNegative = () => {
  if (display.value.at(0) !== '-') {
    display.value = ''.concat('-', display.value)
  } else {
    display.value = display.value.slice(1)
  }
}

const oneDividedBySelected = () => {
  display.value = (1 / eval(display.value)).toString()
}

const squareSelected = () => {
  let val = eval(display.value)
  display.value = (val * val).toString()
}

const squareRootSelected = () => {
  display.value = Math.sqrt(eval(display.value)).toString()
}
</script>

<template>
  <div class="w-full h-auto max-h-screen flex-center gap-4 justify-between">
    <div class="w-fit md:w-1/2 flex flex-col gap-4">
      <!-- Calculator display -->
      <div class="flex-center">
        <input
          v-model="display"
          @keyup.enter="calculate"
          class="size-16 w-full ui-button focus:ring-0 focus:border-none focus:shadow-md focus:shadow-indigo-800"
          type="text"
          name="calculator-display"
          id="calculator-display"
        />
      </div>

      <!-- calculator buttons -->
      <div class="grid grid-cols-4 gap-4">
        <div class="calculator-button">%</div>
        <div @click="clearDisplay" class="calculator-button">C</div>

        <!-- TODO -->
        <!-- back space logo -->
        <div @click="backSpace" class="calculator-button col-span-2">BS</div>

        <div @click="oneDividedBySelected" class="calculator-button">1/x</div>
        <div @click="squareSelected" class="calculator-button">x<sup>2</sup></div>
        <div @click="squareRootSelected" class="calculator-button">x<sup>1/2</sup></div>
        <div @click="clicked('/')" class="calculator-button">/</div>

        <div @click="clicked('7')" class="calculator-button">7</div>
        <div @click="clicked('8')" class="calculator-button">8</div>
        <div @click="clicked('9')" class="calculator-button">9</div>
        <div @click="clicked('*')" class="calculator-button">*</div>

        <div @click="clicked('4')" class="calculator-button">4</div>
        <div @click="clicked('5')" class="calculator-button">5</div>
        <div @click="clicked('6')" class="calculator-button">6</div>
        <div @click="clicked('-')" class="calculator-button">-</div>

        <div @click="clicked('1')" class="calculator-button">1</div>
        <div @click="clicked('2')" class="calculator-button">2</div>
        <div @click="clicked('3')" class="calculator-button">3</div>
        <div @click="clicked('+')" class="calculator-button">+</div>

        <div @click="toggleNegative()" class="calculator-button">+/-</div>
        <div @click="clicked('0')" class="calculator-button">0</div>
        <div @click="clicked('.')" class="calculator-button">.</div>
        <div @click="calculate" class="calculator-button">=</div>
      </div>
    </div>
  </div>
</template>
