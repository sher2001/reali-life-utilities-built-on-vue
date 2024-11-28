<script setup></script>

<template>
  <div class="w-full h-auto max-h-screen flex-center gap-4 justify-between">
    <div class="flex flex-col gap-4">
      <!-- Calculator display -->
      <div class="flex-center">
        <input
          class="size-16 w-full ui-button focus:ring-0 focus:border-none focus:shadow-md focus:shadow-indigo-800"
          type="text"
          name="calculator-display"
          id="calculator-display"
        />
      </div>

      <!-- calculator buttons -->
      <div class="grid grid-cols-4 gap-4">
        <div class="calculator-button">%</div>
        <div class="calculator-button">CE</div>
        <div class="calculator-button">C</div>

        <!-- TODO -->
        <!-- back space logo -->
        <div class="calculator-button">BS</div>

        <div class="calculator-button">1/x</div>
        <div class="calculator-button">x<sup>2</sup></div>
        <div class="calculator-button">x<sup>1/2</sup></div>
        <div class="calculator-button">/</div>

        <div class="calculator-button">7</div>
        <div class="calculator-button">8</div>
        <div class="calculator-button">9</div>
        <div class="calculator-button">*</div>

        <div class="calculator-button">4</div>
        <div class="calculator-button">5</div>
        <div class="calculator-button">6</div>
        <div class="calculator-button">-</div>

        <div class="calculator-button">1</div>
        <div class="calculator-button">2</div>
        <div class="calculator-button">3</div>
        <div class="calculator-button">+</div>

        <div class="calculator-button">+/-</div>
        <div class="calculator-button">0</div>
        <div class="calculator-button">.</div>
        <div class="calculator-button">=</div>
      </div>
    </div>
  </div>
</template>
