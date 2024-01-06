<!-- eslint-disable no-unused-vars -->
<script setup>
import { reactive, ref, } from 'vue'

if (localStorage.getItem('lang') == null) {
  localStorage.setItem('lang', 'uz')

}
const lang = ref(localStorage.getItem('lang'))
const initialLetterLength = 5000
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
const kr = reactive({
  'а': 'a',
  'б': 'b',
  'с': 's',
  'д': 'd',
  'е': 'e',
  'ф': 'f',
  'г': 'g',
  'х': 'h',
  'и': 'i',
  'ж': 'j',
  'к': 'k',
  'л': 'l',
  'м': 'm',
  'н': 'n',
  'о': 'o',
  'п': 'p',
  'р': 'r',
  'т': 't',
  'у': 'u',
  'в': 'v',
  'з': 'z',
  'ш': 'sh',
  'щ': 'sh',
  'ч': 'ch',
  'ъ': '',
  'ы': 'y',
  'э': 'e',
  'ю': 'yu',
  'я': 'ya',
  'ҳ': 'h',
  'қ': 'q',
  'ғ': 'g',
  'ц': 'c',
  "А": "A",
  "Б": "B",
  "С": "C",
  "Д": "D",
  "Е": "E",
  "Ф": "F",
  "Г": "G",
  "Х": "H",
  "И": "I",
  "Ж": "J",
  "К": "K",
  "Л": "L",
  "М": "M",
  "Н": "N",
  "О": "O",
  "П": "P",
  "Р": "R",
  "Т": "T",
  "У": "U",
  "В": "V",
  "З": "Z",
  "Ш": "Sh",
  "Щ": "Sh",
  "Ч": "Ch",
  "Ъ": "",
  "Ы": "Y",
  "Э": "E",
  "Ю": "Yu",
  "Я": "Ya",
  "Ҳ": "H",
  "Қ": "Q",
  "Ғ": "G",
  "Ц": "C",
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
  localStorage.setItem('lang', String(e))
  lang.value = localStorage.getItem('lang')
  gap.value = ""
  document.getElementById('message').value = ""

}


const InpValueUz = (e) => {

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

const InpValueKr = (e) => {
  let data = ""
  if (e.length > 0 && e.length <= initialLetterLength) {
    for (let i = 0; i < e.length; i++) {
      for (const key in kr) {
        if (e[i] == key) {
          data += e[i]
        }
      }
    }
    for (let i = 0; i < e.length; i++) {
      for (const key in kr) {
        data = data.replace(key, kr[key])
      }
      gap.value = data
    }

  }
}

async function copyURL(mytext) {
  try {
    await navigator.clipboard.writeText(mytext);

  } catch ($e) {
    alert('Cannot copy');
  }
}

</script>

<template>
  <main>
    <nav class="bg-gray-900 py-5 mb-5">
      <div class="container mx-auto text-center">
        <h1 class="text-white text-2xl font-bold uppercase font-mono">{{ lang == 'uz' ? 'Lotin-Krill' : 'Крил-Лотин' }}
        </h1>
      </div>
    </nav>
    <div class="container px-4 mx-auto py-4">
      <!-- Language buttons group -->
      <div class=" flex gap-2">
        <button
          :class="lang == 'uz' ? 'bg-blue-500 w-full  text-white font-bold py-2 px-4 rounded border-blue-500 ' : 'bg-transparent border-blue-500 text-blue-500 w-full font-bold py-2 px-4 rounded '"
          @click="Language('uz')" class="font-mono border-2 text-lg active:scale-[0.99] duration-300">Lotin-Krill</button>
        <button
          :class="lang == 'kr' ? 'bg-blue-500 w-full text-white font-bold py-2 px-4 rounded border-blue-500' : 'bg-transparent border-blue-500 text-blue-500 font-bold py-2 px-4 rounded w-full'"
          @click="Language('kr')" class="font-mono text-lg active:scale-[0.99] duration-300 border-2">Крил-Лотин</button>
      </div>
    </div>
    <div class="container px-4 mx-auto py-5  grid grid-cols-1 gap-4 md:grid-cols-2">
      <div class="w-full">
        <textarea id="message" rows="16" @input="(e) => {
          if (lang == 'uz') {
            InpValueUz(e.target.value)
          }
          if (lang == 'kr') {
            InpValueKr(e.target.value)
          }
        }"
          class="block p-2.5 w-full text-sm font-mono text-gray-900 rounded-lg  border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          :placeholder="lang == 'uz' ? 'Matn kiriting...' : 'Матнни киритинг...'"
          :class="gap.length >= initialLetterLength ? 'bg-gray-200 outline-red-500 border-2 border-red-500' : ' bg-gray-50 border'"></textarea>
        <div class="flex justify-between py-2 font-mono">
          <p class="text-red-500">{{ gap.length >= initialLetterLength ? lang == 'uz' ? "Malumotlarni kamaytiring!" :
            'Малумотларни камайтинг!' : "" }}</p>
          <p class="flex justify-end">{{ gap.length }} / {{ initialLetterLength }}</p>
        </div>
        <button @click="gap = ''" onclick="document.getElementById('message').value = ''"
          class="bg-blue-500 border-2 border-blue-500  text-white font-mono py-2 px-4 rounded hover:bg-transparent hover:text-blue-500 duration-300 active:scale-95">{{
            lang == 'uz' ? 'Tozalash' : 'Тозалаш' }}</button>
      </div>
      <div class="w-full">
        <textarea id="message" rows="16" v-model="gap"
          class="block p-2.5 w-full text-sm font-mono text-gray-900 bg-gray-200 rounded-lg border border-gray-300"
          :placeholder="lang == 'uz' ? '' : ''" disabled></textarea>
        <div class="flex md:justify-end  font-mono mt-10">
          <button @click="copyURL(gap)"
            class="  bg-emerald-500 border-2 border-emerald-500  text-white font-mono py-2 px-4 rounded hover:bg-transparent hover:text-emerald-500 duration-300 active:scale-95 active:bg-emerald-500 active:text-white">
            {{ lang == 'uz' ? `Nusxa
            olish` : 'Нусха олиш' }}
          </button>
        </div>
      </div>


    </div>


    <footer class="bg-gray-900 py-5">
      <div class="container mx-auto text-center">
        <p class="text-gray-400 font-mono">{{ lang == 'uz' ? 'Developer' : 'Девелопер' }} <a class=" text-white"
            href="https://github.com/JavohirBozorboyev">{{ lang == 'uz' ? 'Javohir Bozorboyev' : 'Жавохир Бозорбойев'
            }}</a>

        </p>
      </div>
    </footer>

  </main>
</template>
