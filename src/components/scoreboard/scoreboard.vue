<template>
  <div class="card font-source">
    <div class="flex justify-between gap-5 items-center">
      <div class="flex items-center">
        <img :src="fixture.league.logo" :alt="fixture.league.name" class="w-10 h-auto ltr:mr-4 rtl:ml-4"/>
        <div class="leading-5 uppercase font-source">
          <span class="text-purple-950 font-normal text-sm">{{ fixture.league.country }} : {{ fixture.league.name }}</span>
          <h1 class="text-xl font-black">{{ fixture.teams.home.name }} VS {{ fixture.teams.away.name }}</h1>
          <span class="text-sm">LIVE score and LIVE stream</span>
        </div>
      </div>
      <!-- Toggle Notifications -->
      <Switch
        v-model="enabled"
        :class="enabled ? 'bg-blue-600' : 'bg-gray-200'"
        class="relative inline-flex h-10 w-16 items-center rounded-full"
      >
        <span class="sr-only">Enable notifications</span>
        <span
          :class="enabled ? 'ltr:translate-x-1 rtl:-translate-x-1' : 'ltr:translate-x-6 rtl:-translate-x-6'"
          class="flex items-center justify-center h-8 w-8 transform rounded-full bg-white transition"
        >
          <span :class="bellClass">
            <svg xmlns="http://www.w3.org/2000/svg" id="Capa_1" enable-background="new 0 0 512 512" height="512" viewBox="0 0 512 512" width="512"
                class="w-6 h-auto opacity-30">
            <path d="m450.201 407.453c-1.505-.977-12.832-8.912-24.174-32.917-20.829-44.082-25.201-106.18-25.201-150.511 0-.193-.004-.384-.011-.576-.227-58.589-35.31-109.095-85.514-131.756v-34.657c0-31.45-25.544-57.036-56.942-57.036h-4.719c-31.398 0-56.942 25.586-56.942 57.036v34.655c-50.372 22.734-85.525 73.498-85.525 132.334 0 44.331-4.372 106.428-25.201 150.511-11.341 24.004-22.668 31.939-24.174 32.917-6.342 2.935-9.469 9.715-8.01 16.586 1.473 6.939 7.959 11.723 15.042 11.723h109.947c.614 42.141 35.008 76.238 77.223 76.238s76.609-34.097 77.223-76.238h109.947c7.082 0 13.569-4.784 15.042-11.723 1.457-6.871-1.669-13.652-8.011-16.586zm-223.502-350.417c0-14.881 12.086-26.987 26.942-26.987h4.719c14.856 0 26.942 12.106 26.942 26.987v24.917c-9.468-1.957-19.269-2.987-29.306-2.987-10.034 0-19.832 1.029-29.296 2.984v-24.914zm29.301 424.915c-25.673 0-46.614-20.617-47.223-46.188h94.445c-.608 25.57-21.549 46.188-47.222 46.188zm60.4-76.239c-.003 0-213.385 0-213.385 0 2.595-4.044 5.236-8.623 7.861-13.798 20.104-39.643 30.298-96.129 30.298-167.889 0-63.417 51.509-115.01 114.821-115.01s114.821 51.593 114.821 115.06c0 .185.003.369.01.553.057 71.472 10.25 127.755 30.298 167.286 2.625 5.176 5.267 9.754 7.861 13.798z"/>
            </svg>
          </span>
        </span>
      </Switch>
    </div>
    <div class="flex justify-center text-xl font-black mt-6">
      <div class="flex-1 flex flex-col items-center">
          <div class="w-16 shrink-0 mb-2">
            <img :src="fixture.teams.home.logo" :alt="fixture.teams.home.name" />
          </div>
          <div class="text-center uppercase">{{fixture.teams.home.name}}</div>
      </div>
      <div class="flex flex-col items-center font-bold">
        <div class="uppercase text-red-500 font-cairo">{{ datefix.toRelative() }}</div>
        <div class="text-gray-500 text-3xl">{{ datefix.setLocale('fr').toLocaleString(DateTime.TIME_SIMPLE) }}</div>
      </div>
      <div class="flex-1 flex flex-col items-center">
          <div class="w-16 shrink-0 mb-2">
            <img :src="fixture.teams.away.logo" :alt="fixture.teams.home.name" />
          </div>
          <div class="text-center uppercase">{{fixture.teams.away.name}}</div>
      </div>
    </div>
    <div class="flex justify-center text-gray-400 font-cairo text-sm mt-2">
      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2">
        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v6h4.5m4.5 0a9 9 0 11-18 0 9 9 0 0118 0z" />
      </svg>
      {{ datefix.toLocaleString(DateTime.DATE_HUGE) }}
    </div>
  </div>
</template>
<script setup>
import { DateTime } from "luxon"
import { onMounted, ref } from "vue";
import { Switch } from "@headlessui/vue"

defineProps({
    teams: Object,
    formation: String
})
const bellClass = ref('SubscribeButtonAnimated')
const enabled = ref(false)
const fixture = 
{
"fixture": {
  "id": 239625,
  "referee": null,
  "timezone": "UTC",
  "date": "2020-02-06T14:00:00+00:00",
  "timestamp": 1580997600,
  "periods": {
    "first": 1580997600,
    "second": null
  },
  "venue": {
    "id": 1887,
    "name": "Stade Municipal",
    "city": "Oued Zem"
  },
  "status": {
    "long": "Halftime",
    "short": "HT",
    "elapsed": 45
  }
},
"league": {
  "id": 200,
  "name": "Botola Pro",
  "country": "Morocco",
  "logo": "https://media.api-sports.io/football/leagues/115.png",
  "flag": "https://media.api-sports.io/flags/ma.svg",
  "season": 2019,
  "round": "Regular Season - 14"
},
"teams": {
  "home": {
    "id": 967,
    "name": "Rapide Oued ZEM",
    "logo": "https://media.api-sports.io/football/teams/967.png",
    "winner": false
  },
  "away": {
    "id": 968,
    "name": "Wydad AC",
    "logo": "https://media.api-sports.io/football/teams/968.png",
    "winner": true
  }
},
"goals": {
  "home": 0,
  "away": 1
},
"score": {
  "halftime": {
    "home": 0,
    "away": 1
  },
  "fulltime": {
    "home": null,
    "away": null
  },
  "extratime": {
    "home": null,
    "away": null
  },
  "penalty": {
    "home": null,
    "away": null
  }
}
  }
onMounted(() => {
  setInterval(() => {
    bellClass.value = bellClass.value === 'SubscribeButtonAnimated' ? '' : 'SubscribeButtonAnimated';
  }, 5000)
})
let datefix = DateTime.fromISO(fixture.fixture.date).setLocale('ar')

</script>
<style lang="css">
/*@import "./scoreboard.scss";*/
.toggle-path {
    transition: background 0.3s ease-in-out;
}
.toggle-circle {
    top: 0.25rem;
    left: 0.25rem;
    transition: all 0.3s ease-in-out;
}
input:checked ~ .toggle-circle {
    transform: translateX(50%);
}
input:checked ~ .toggle-path {
    background-color:#81E6D9;
}
.SubscribeButtonAnimated {
    animation: bell 2s infinite ease-out;
    transform-origin: center top
}

.SubscribeButtonAnimatedOnce .SubscribeButtonRing {
    animation-iteration-count: 1
}


@keyframes bell {
    0% {
        transform: rotate(35deg)
    }

    6.25% {
        transform: rotate(-30deg)
    }

    12.5% {
        transform: rotate(25deg)
    }

    18.75% {
        transform: rotate(-20deg)
    }

    25% {
        transform: rotate(15deg)
    }

    31.25% {
        transform: rotate(-10deg)
    }

    37.5% {
        transform: rotate(5deg)
    }

    50% {
        transform: rotate(0)
    }

    100% {
        transform: rotate(0)
    }
}
</style>