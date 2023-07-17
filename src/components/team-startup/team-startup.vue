<template>
  <div dir="ltr" class="hidden md:flex flex-row-reverse gap-5 mt-4 p-4 font-[Montserrat]">
    <div class="w-full rounded-xl border shadow-md" v-for="team in teams" v-bind:key="team.name">
      <div class="flex items-center h-12 text-2xl font-bold">
        <span
          class="float-left block w-3 h-full rounded-tl-xl"
          :style="{ 'background-color': '#' + team.team.colors.player.primary }"
        ></span>
        <span class="mx-3">{{ team.team.name }}</span>
        <span class="text-base">{{ team.formation }}</span>
        <span class="ml-auto mr-2"
          ><img class="w-auto h-[40px]" :src="team.team.logo" :alt="`${team.team.name} logo`"
        /></span>
      </div>
      <div class="team-lineup">
        <table class="w-full">
          <tr class=" bg-gray-100">
            <td colspan="2" class="uppercase font-bold py-2">coach</td>
          </tr>
          <tr class="bg-white border-b">
            <td></td>
            <td class="py-2">{{ team.coach.name }}</td>
          </tr>
          <tr class="bg-gray-100">
            <td colspan="2" class="uppercase font-bold py-2">starting XI</td>
          </tr>
          <tr class="font-light" v-for="player in team.startXI" :key="player.player.name">
            <td class="py-2 w-1/6 text-gray-500">{{ player.player.number }}</td>
            <td class="py-2">{{ player.player.name }}</td>
          </tr>
          <tr class="bg-gray-100">
            <td colspan="2" class="uppercase font-bold py-2">substitutes</td>
          </tr>
          <tr class="font-light" v-for="player in team.substitutes" :key="player.player.name">
            <td class="py-2 w-1/6 text-gray-500">{{ player.player.number }}</td>
            <td class="py-2">{{ player.player.name }}</td>
          </tr>
        </table>

        
      </div>
    </div>
  </div>
  <div class="flex flex-col md:hidden gap-5 mt-4 p-4 font-source">
    <TabGroup>
      <TabList class="w-full flex space-x-1 rounded-xl bg-blue-900/20 p-1">
        <Tab
          v-for="team in teams"
          as="template"
          :key="team.team.id"
          v-slot="{ selected }"
        >
          <button
            :class="[
              'w-full rounded-lg py-2.5 text-sm font-medium leading-5 text-blue-700',
              'ring-white ring-opacity-60 ring-offset-2 ring-offset-blue-400 focus:outline-none focus:ring-2',
              selected
                ? 'bg-white shadow'
                : 'text-blue-100 hover:bg-white/[0.12] hover:text-white',
            ]"
          >
            {{ team.team.name }}
        </button>
        </Tab>
      </TabList>
      <TabPanels class="mt-2">
        <TabPanel v-slot="{selected}" v-for="(team, idx) in teams"
          :key="idx"
          :class="[
            'rounded-xl bg-white p-3',
            'ring-white ring-opacity-60 ring-offset-2 ring-offset-blue-400 focus:outline-none focus:ring-2',
          ]">
          <TransitionRoot appear :show="selected"
                            enter="transition-opacity duration-500"
                            enterFrom="opacity-0"
                            enterTo="opacity-100"
                            leave="transition-opacity duration-500"
                            leaveFrom="opacity-100"
                            leaveTo="opacity-0">
          <table class="w-full">
          <tr class=" bg-gray-100">
            <td colspan="2" class="text-center uppercase font-bold py-2">coach</td>
          </tr>
          <tr class="bg-white border-b">
            <td></td>
            <td class="py-2">{{ team.coach.name }}</td>
          </tr>
          <tr class="bg-gray-100">
            <td colspan="2" class="text-center uppercase font-bold py-2">starting XI</td>
          </tr>
          <tr class="font-light" v-for="player in team.startXI" :key="player.player.name">
            <td class="py-2 w-1/6 text-gray-500">{{ player.player.number }}</td>
            <td class="py-2">{{ player.player.name }}</td>
          </tr>
          <tr class="bg-gray-100">
            <td colspan="2" class="text-center uppercase font-bold py-2">substitutes</td>
          </tr>
          <tr class="font-light" v-for="player in team.substitutes" :key="player.player.name">
            <td class="py-2 w-1/6 text-gray-500">{{ player.player.number }}</td>
            <td class="py-2">{{ player.player.name }}</td>
          </tr>
        </table>
        </TransitionRoot>
        </TabPanel>
      </TabPanels>
    </TabGroup>
  </div>
</template>
<script setup>
import { TabGroup, TabList, Tab, TabPanels, TabPanel, TransitionRoot } from '@headlessui/vue';

defineProps({
  teams: Object,
  formation: String,
})
</script>
<style lang="css">
table > tr > td { padding-left: 1.25rem; }
</style>