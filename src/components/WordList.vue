<script setup lang="ts">
import { generate } from "random-words";

const props = defineProps(["typedWords"]);
const wordList = generate(200);
</script>

<template>
  <div
    class="flex mt-10 text-white/40 flex-wrap gap-x-5 gap-y-2.5 azeret text-2xl w-[80vw] h-20 overflow-hidden"
  >
    <span
      :class="{
        'text-lime-400': props.typedWords?.[i] === wordList[i],
        'text-red-400':
          props.typedWords?.[i] !== wordList[i] && props.typedWords.length > i,
      }"
      v-for="(word, i) in wordList"
      :key="i"
      >{{ word }}</span
    >
  </div>
</template>
