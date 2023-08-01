<script setup lang="ts">
import { ref } from "vue";

const props = defineProps(["lastLetter"]);
const firstRow = ["q", "w", "e", "r", "t", "y", "u", "i", "o", "p"];
const secondRow = ["a", "s", "d", "f", "g", "h", "j", "k", "l"];
const thirdRow = ["z", "x", "c", "v", "b", "n", "m"];
</script>

<template>
  <div class="flex flex-col gap-2.5 items-center justify-center">
    <div class="flex gap-5 azeret">
      <div
        v-for="letter in firstRow"
        class="p-5 rounded-full bg-black text-xl"
        :class="{ 'bg-lime-400 text-black': props.lastLetter === letter }"
      >
        {{ letter }}
      </div>
    </div>
    <div class="flex gap-5 azeret">
      <div
        v-for="letter in secondRow"
        class="p-5 rounded-full bg-black text-xl"
        :class="{ 'bg-lime-400 text-black': props.lastLetter === letter }"
      >
        {{ letter }}
      </div>
    </div>
    <div class="flex gap-5 azeret">
      <div
        v-for="letter in thirdRow"
        class="p-5 rounded-full bg-black text-xl"
        :class="{ 'bg-lime-400 text-black': props.lastLetter === letter }"
      >
        {{ letter }}
      </div>
    </div>
    <div
      class="w-96 bg-black h-16 rounded-full"
      :class="{ 'bg-lime-400 text-black': props.lastLetter === ' ' }"
    ></div>
  </div>
</template>
