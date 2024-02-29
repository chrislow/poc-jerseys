<script setup lang="ts">
import { ref } from 'vue'
import SingleJersey from './components/SingleJersey.vue'
import PrimaryButton from './components/PrimaryButton.vue'
import matches from './assets/json/matches.json'

const match = ref(matches[0])

const changeMatch = (index: number) => {
  match.value = matches[index]
}
</script>

<template>
  <main class="w-[500px] mx-auto p-8">
    <div class=" flex flex-col gap-4 mb-16">
      <primary-button @click="changeMatch(0)">Match 1</primary-button>
      <primary-button @click="changeMatch(1)">Match 2</primary-button>
      <primary-button @click="changeMatch(2)">Match 3</primary-button>
    </div>
    <div class="flex flex-col gap-8">
      <div class="flex gap-8">
        <single-jersey :base="'#' + match.jerseys.home.player.base" :sleeve="'#' + match.jerseys.home.player.sleeve"
                       :number="'#' + match.jerseys.home.player.number" :type="'#' + match.jerseys.home.player.type"
                       :sleevelong="'#' + match.jerseys.home.player.sleevelong"
                       :real="match.jerseys.home.player.real"></single-jersey>
        <single-jersey :base="'#' + match.jerseys.away.player.base" :sleeve="'#' + match.jerseys.away.player.sleeve"
                       :number="'#' + match.jerseys.away.player.number" :type="'#' + match.jerseys.away.player.type"
                       :sleevelong="'#' + match.jerseys.away.player.sleevelong"
                       :real="match.jerseys.away.player.real"></single-jersey>
      </div>
      <div class="w-full text-center font-bold">
        <p>{{ match.title }}</p>
      </div>
    </div>
  </main>
</template>
