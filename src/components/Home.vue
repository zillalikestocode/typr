<script setup lang="ts">
import { reactive, ref } from "vue";
import Keyboard from "./Keyboard.vue";
import { generate } from "random-words";
import WordList from "./WordList.vue";

const lastLetter = ref("");
const currentWord = ref("");
const typedWords = reactive<{ words: string[] }>({ words: [] });

function changeLast(e: KeyboardEvent) {
  lastLetter.value = e.key;
}

function spaceFunction(e: KeyboardEvent) {
  lastLetter.value = e.key;
  typedWords.words.push(currentWord.value);
  currentWord.value = "";
  console.log(typedWords.words);
}
</script>

<template>
  <div class="flex flex-col items-center justify-center">
    <WordList :typed-words="typedWords.words" />
    <div class="p-10">
      <input
        v-model="currentWord"
        @input="e => {if((e.target as HTMLInputElement).value === ' '){
            currentWord = ''
        }}"
        spellcheck="false"
        autofocus
        class="bg-transparent w-[500px] text-center tracking-wide azeret focus:outline-none text-3xl text-white"
        @keydown.space="spaceFunction"
        @keydown="changeLast"
      />
    </div>
    <Keyboard :last-letter="lastLetter" />
  </div>
</template>
