<!-- eslint-disable no-unused-vars -->
<script setup>
import { reactive, ref, } from 'vue'

const lang = ref('uz')
const initialLetterLength = 1000
const uz = reactive({
  a: 'а',
  b: 'б',
  c: 'с',
  d: 'д',
  e: 'е',
  f: 'ф',
  g: 'г',
  h: 'х',
  i: 'и',
  j: 'ж',
  k: 'к',
  l: 'л',
  m: 'м',
  n: 'н',
  o: 'о',
  p: 'п',
  q: 'к',
  r: 'р',
  s: 'с',
  t: 'т',
  u: 'у',
  v: 'в',
  w: 'в',
  x: 'х',
  y: 'и',
  z: 'з',
  A: 'А',
  B: 'Б',
  C: 'С',
  D: 'Д',
  E: 'Е',
  F: 'Ф',
  G: 'Г',
  H: 'Х',
  I: 'И',
  J: 'Ж',
  K: 'К',
  L: 'Л',
  M: 'М',
  N: 'Н',
  O: 'О',
  P: 'П',
  Q: 'К',
  R: 'Р',
  S: 'С',
  T: 'Т',
  U: 'У',
  V: 'В',
  W: 'В',
  X: 'Х',
  Y: 'И',
  Z: 'З',
  ' ': ' ',
  ',': ',',
  '.': '.',
  '-': '-',
  '+': '+',
  '*': '*',
  '/': '/',
  '=': '=',
  '(': '(',
  ')': ')',
  '[': '[',
  ']': ']',
  '{': '{',
  '}': '}',
  ';': ';',
  ':': ':',
  "'": "'",
  '"': '"',
  '<': '<',
  '>': '>',
  '?': '?',
  '!': '!',
  '@': '@',
  '#': '#',
  '$': '$',
  '%': '%',
  '^': '^',
  '&': '&',
  '0': '0',
  '1': '1',
  '2': '2',
  '3': '3',
  '4': '4',
  '5': '5',
  '6': '6',
  '7': '7',
  '8': '8',
  '9': '9',
})
let gap = ref("")

const Language = (e) => {
  lang.value = e
  gap.value = ""

}


const InpValue = (e) => {

  let data = ""

  if (e.length > 0 && e.length <= initialLetterLength) {
    for (let i = 0; i < e.length; i++) {

      for (const key in uz) {

        if (e[i] == key) {
          data += e[i]
          if (data.includes("sh")) {
            data = data.replace("sh", "ш")
          }
          if (data.includes("ch")) {
            data = data.replace("ch", "ч")
          }
          if (data.includes("yu")) {
            data = data.replace("yu", "ю")
          }
          if (data.includes("ya")) {
            data = data.replace("ya", "я")

          }
          if (data.includes("yo")) {
            data = data.replace("yo", "е")

          }

        }
      }

    }

    for (let i = 0; i < e.length; i++) {
      for (const key in uz) {
        data = data.replace(key, uz[key])
      }
      gap.value = data

    }

  }

  if (e.length == 0) {
    gap.value = ''

  }
}













</script>

<template>
  <main>
    <div class="container px-4 mx-auto py-10 ">
      <!-- Language buttons group -->
      <div class="bg-gray-100  p-2 rounded-md flex gap-2">
        <button
          :class="lang == 'uz' ? 'bg-blue-500 w-full  text-white font-bold py-2 px-4 rounded ' : 'bg-gray-400 text-white w-full font-bold py-2 px-4 rounded '"
          @click="Language('uz')">Lotin-Krill</button>
        <button
          :class="lang == 'kr' ? 'bg-blue-500 w-full text-white font-bold py-2 px-4 rounded' : 'bg-gray-400 text-white font-bold py-2 px-4 rounded w-full'"
          @click="Language('kr')">Крил-Лотин</button>
      </div>
    </div>
    <div class="container px-4 mx-auto py-5  grid grid-cols-1 gap-4 md:grid-cols-2">
      <div class="w-full">
        <textarea id="message" rows="16" @input="InpValue($event.target.value)"
          class="block p-2.5 w-full text-sm text-gray-900 rounded-lg  border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Uzbekcha matn kiriting..."
          :class="gap.length >= initialLetterLength ? 'bg-gray-200 outline-red-500 border-2 border-red-500' : ' bg-gray-50 border'"></textarea>
        <div class="flex justify-between py-2">
          <p class="text-red-500">{{ gap.length >= initialLetterLength ? "Malumotlarni kamaytiring!" : "" }}</p>
          <p class="flex justify-end">{{ gap.length }} / {{ initialLetterLength }}</p>
        </div>
      </div>
      <div class="w-full">
        <textarea id="message" rows="16" v-model="gap"
          class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          :placeholder="lang == 'uz' ? '' : ''" :disabled="lang == 'uz'"></textarea>
      </div>


    </div>



  </main>
</template>
