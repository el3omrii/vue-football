<script setup>
import Pitch from './components/pitch'
import Scoreboard from './components/scoreboard'
import TeamStartup from './components/team-startup'
import { TabGroup, TabList, Tab, } from '@headlessui/vue'

const tabs = [
  { name: 'Home',
    class: 'w-full hover:text-red-500 hover:bg-gray-200 ring-offset-blue-400 focus:outline-none focus:ring-2 py-2 uppercase'
  },
  { name: 'Line Up',
  class: 'w-full hover:text-red-500 hover:bg-gray-200 ring-offset-blue-400 focus:outline-none focus:ring-2 py-2 uppercase'
  },
  { name: 'Stats',
  class: 'w-full hover:text-red-500 hover:bg-gray-200 ring-offset-blue-400 focus:outline-none focus:ring-2 py-2 uppercase'
  }
]
const teams = [
    {
      "team": {
        "id": 50,
        "name": "Manchester City",
        "logo": "https://media.api-sports.io/football/teams/50.png",
        "colors": {
          "player": {
            "primary": "5badff",
            "number": "ffffff",
            "border": "99ff99"
          },
          "goalkeeper": {
            "primary": "99ff99",
            "number": "000000",
            "border": "99ff99"
          }
        }
      },
      "formation": "4-3-3",
      "startXI": [
        {
          "player": {
            "id": 617,
            "name": "Ederson",
            "number": 31,
            "pos": "G",
            "grid": "1:1"
          }
        },
        {
          "player": {
            "id": 627,
            "name": "Kyle Walker",
            "number": 2,
            "pos": "D",
            "grid": "2:4"
          }
        },
        {
          "player": {
            "id": 626,
            "name": "John Stones",
            "number": 5,
            "pos": "D",
            "grid": "2:3"
          }
        },
        {
          "player": {
            "id": 567,
            "name": "Rúben Dias",
            "number": 3,
            "pos": "D",
            "grid": "2:2"
          }
        },
        {
          "player": {
            "id": 641,
            "name": "Oleksandr Zinchenko",
            "number": 11,
            "pos": "D",
            "grid": "2:1"
          }
        },
        {
          "player": {
            "id": 629,
            "name": "Kevin De Bruyne",
            "number": 17,
            "pos": "M",
            "grid": "3:3"
          }
        },
        {
          "player": {
            "id": 640,
            "name": "Fernandinho",
            "number": 25,
            "pos": "M",
            "grid": "3:2"
          }
        },
        {
          "player": {
            "id": 631,
            "name": "Phil Foden",
            "number": 47,
            "pos": "M",
            "grid": "3:1"
          }
        },
        {
          "player": {
            "id": 635,
            "name": "Riyad Mahrez",
            "number": 26,
            "pos": "F",
            "grid": "4:3"
          }
        },
        {
          "player": {
            "id": 643,
            "name": "Gabriel Jesus",
            "number": 9,
            "pos": "F",
            "grid": "4:2"
          }
        },
        {
          "player": {
            "id": 645,
            "name": "Raheem Sterling",
            "number": 7,
            "pos": "F",
            "grid": "4:1"
          }
        }
      ],
      "substitutes": [
        {
          "player": {
            "id": 50828,
            "name": "Zack Steffen",
            "number": 13,
            "pos": "G",
            "grid": null
          }
        },
        {
          "player": {
            "id": 623,
            "name": "Benjamin Mendy",
            "number": 22,
            "pos": "D",
            "grid": null
          }
        },
        {
          "player": {
            "id": 18861,
            "name": "Nathan Aké",
            "number": 6,
            "pos": "D",
            "grid": null
          }
        },
        {
          "player": {
            "id": 622,
            "name": "Aymeric Laporte",
            "number": 14,
            "pos": "D",
            "grid": null
          }
        },
        {
          "player": {
            "id": 633,
            "name": "İlkay Gündoğan",
            "number": 8,
            "pos": "M",
            "grid": null
          }
        },
        {
          "player": {
            "id": 44,
            "name": "Rodri",
            "number": 16,
            "pos": "M",
            "grid": null
          }
        },
        {
          "player": {
            "id": 931,
            "name": "Ferrán Torres",
            "number": 21,
            "pos": "F",
            "grid": null
          }
        },
        {
          "player": {
            "id": 636,
            "name": "Bernardo Silva",
            "number": 20,
            "pos": "M",
            "grid": null
          }
        },
        {
          "player": {
            "id": 642,
            "name": "Sergio Agüero",
            "number": 10,
            "pos": "F",
            "grid": null
          }
        }
      ],
      "coach": {
        "id": 4,
        "name": "Guardiola",
        "photo": "https://media.api-sports.io/football/coachs/4.png"
      }
    },
    {
      "team": {
        "id": 45,
        "name": "Everton",
        "logo": "https://media.api-sports.io/football/teams/45.png",
        "colors": {
          "player": {
            "primary": "070707",
            "number": "ffffff",
            "border": "66ff00"
          },
          "goalkeeper": {
            "primary": "66ff00",
            "number": "000000",
            "border": "66ff00"
          }
        }
      },
      "formation": "4-3-1-2",
      "startXI": [
        {
          "player": {
            "id": 2932,
            "name": "Jordan Pickford",
            "number": 1,
            "pos": "G",
            "grid": "1:1"
          }
        },
        {
          "player": {
            "id": 19150,
            "name": "Mason Holgate",
            "number": 4,
            "pos": "D",
            "grid": "2:4"
          }
        },
        {
          "player": {
            "id": 2934,
            "name": "Michael Keane",
            "number": 5,
            "pos": "D",
            "grid": "2:3"
          }
        },
        {
          "player": {
            "id": 19073,
            "name": "Ben Godfrey",
            "number": 22,
            "pos": "D",
            "grid": "2:2"
          }
        },
        {
          "player": {
            "id": 2724,
            "name": "Lucas Digne",
            "number": 12,
            "pos": "D",
            "grid": "2:1"
          }
        },
        {
          "player": {
            "id": 18805,
            "name": "Abdoulaye Doucouré",
            "number": 16,
            "pos": "M",
            "grid": "3:3"
          }
        },
        {
          "player": {
            "id": 326,
            "name": "Allan",
            "number": 6,
            "pos": "M",
            "grid": "3:2"
          }
        },
        {
          "player": {
            "id": 18762,
            "name": "Tom Davies",
            "number": 26,
            "pos": "M",
            "grid": "3:1"
          }
        },
        {
          "player": {
            "id": 2795,
            "name": "Gylfi Sigurðsson",
            "number": 10,
            "pos": "M",
            "grid": "4:1"
          }
        },
        {
          "player": {
            "id": 18766,
            "name": "Dominic Calvert-Lewin",
            "number": 9,
            "pos": "F",
            "grid": "5:2"
          }
        },
        {
          "player": {
            "id": 2413,
            "name": "Richarlison",
            "number": 7,
            "pos": "F",
            "grid": "5:1"
          }
        }
      ],
      "substitutes": [
        {
          "player": {
            "id": 18755,
            "name": "João Virgínia",
            "number": 31,
            "pos": "G",
            "grid": null
          }
        },
        {
          "player": {
            "id": 766,
            "name": "Robin Olsen",
            "number": 33,
            "pos": "G",
            "grid": null
          }
        },
        {
          "player": {
            "id": 156490,
            "name": "Niels Nkounkou",
            "number": 18,
            "pos": "D",
            "grid": null
          }
        },
        {
          "player": {
            "id": 18758,
            "name": "Séamus Coleman",
            "number": 23,
            "pos": "D",
            "grid": null
          }
        },
        {
          "player": {
            "id": 138849,
            "name": "Kyle John",
            "number": 48,
            "pos": "D",
            "grid": null
          }
        },
        {
          "player": {
            "id": 18765,
            "name": "André Gomes",
            "number": 21,
            "pos": "M",
            "grid": null
          }
        },
        {
          "player": {
            "id": 1455,
            "name": "Alex Iwobi",
            "number": 17,
            "pos": "F",
            "grid": null
          }
        },
        {
          "player": {
            "id": 18761,
            "name": "Bernard",
            "number": 20,
            "pos": "F",
            "grid": null
          }
        }
      ],
      "coach": {
        "id": 2407,
        "name": "C. Ancelotti",
        "photo": "https://media.api-sports.io/football/coachs/2407.png"
      }
    }
  ]
</script>

<template>
  <header class="header sticky top-0 bg-black shadow-md flex items-center px-8 py-4">
    <!-- logo -->
    <h1 class="w-3/12 text-white">
        <a href="">
          <svg viewBox="0 0 248 31" class="h-6 w-auto hover:text-green-500 duration-200"><path d="M25.517 0C18.712 0 14.46 3.382 12.758 10.146c2.552-3.382 5.529-4.65 8.931-3.805 1.941.482 3.329 1.882 4.864 3.432 2.502 2.524 5.398 5.445 11.722 5.445 6.804 0 11.057-3.382 12.758-10.145-2.551 3.382-5.528 4.65-8.93 3.804-1.942-.482-3.33-1.882-4.865-3.431C34.736 2.92 31.841 0 25.517 0zM12.758 15.218C5.954 15.218 1.701 18.6 0 25.364c2.552-3.382 5.529-4.65 8.93-3.805 1.942.482 3.33 1.882 4.865 3.432 2.502 2.524 5.397 5.445 11.722 5.445 6.804 0 11.057-3.381 12.758-10.145-2.552 3.382-5.529 4.65-8.931 3.805-1.941-.483-3.329-1.883-4.864-3.432-2.502-2.524-5.398-5.446-11.722-5.446z" fill="#22C55E"></path><path fill-rule="evenodd" clip-rule="evenodd" d="M76.546 12.825h-4.453v8.567c0 2.285 1.508 2.249 4.453 2.106v3.463c-5.962.714-8.332-.928-8.332-5.569v-8.567H64.91V9.112h3.304V4.318l3.879-1.143v5.937h4.453v3.713zM93.52 9.112h3.878v17.849h-3.878v-2.57c-1.365 1.891-3.484 3.034-6.285 3.034-4.884 0-8.942-4.105-8.942-9.389 0-5.318 4.058-9.388 8.942-9.388 2.801 0 4.92 1.142 6.285 2.999V9.112zm-5.674 14.636c3.232 0 5.674-2.392 5.674-5.712s-2.442-5.711-5.674-5.711-5.674 2.392-5.674 5.711c0 3.32 2.442 5.712 5.674 5.712zm16.016-17.313c-1.364 0-2.477-1.142-2.477-2.463a2.475 2.475 0 012.477-2.463 2.475 2.475 0 012.478 2.463c0 1.32-1.113 2.463-2.478 2.463zm-1.939 20.526V9.112h3.879v17.849h-3.879zm8.368 0V.9h3.878v26.06h-3.878zm29.053-17.849h4.094l-5.638 17.849h-3.807l-3.735-12.03-3.771 12.03h-3.806l-5.639-17.849h4.094l3.484 12.315 3.771-12.315h3.699l3.734 12.315 3.52-12.315zm8.906-2.677c-1.365 0-2.478-1.142-2.478-2.463a2.475 2.475 0 012.478-2.463 2.475 2.475 0 012.478 2.463c0 1.32-1.113 2.463-2.478 2.463zm-1.939 20.526V9.112h3.878v17.849h-3.878zm17.812-18.313c4.022 0 6.895 2.713 6.895 7.354V26.96h-3.878V16.394c0-2.713-1.58-4.14-4.022-4.14-2.55 0-4.561 1.499-4.561 5.14v9.567h-3.879V9.112h3.879v2.285c1.185-1.856 3.124-2.749 5.566-2.749zm25.282-6.675h3.879V26.96h-3.879v-2.57c-1.364 1.892-3.483 3.034-6.284 3.034-4.884 0-8.942-4.105-8.942-9.389 0-5.318 4.058-9.388 8.942-9.388 2.801 0 4.92 1.142 6.284 2.999V1.973zm-5.674 21.775c3.232 0 5.674-2.392 5.674-5.712s-2.442-5.711-5.674-5.711-5.674 2.392-5.674 5.711c0 3.32 2.442 5.712 5.674 5.712zm22.553 3.677c-5.423 0-9.481-4.105-9.481-9.389 0-5.318 4.058-9.388 9.481-9.388 3.519 0 6.572 1.82 8.008 4.605l-3.34 1.928c-.79-1.678-2.549-2.749-4.704-2.749-3.16 0-5.566 2.392-5.566 5.604 0 3.213 2.406 5.605 5.566 5.605 2.155 0 3.914-1.107 4.776-2.749l3.34 1.892c-1.508 2.82-4.561 4.64-8.08 4.64zm14.472-13.387c0 3.249 9.661 1.285 9.661 7.89 0 3.57-3.125 5.497-7.003 5.497-3.591 0-6.177-1.607-7.326-4.177l3.34-1.927c.574 1.606 2.011 2.57 3.986 2.57 1.724 0 3.052-.571 3.052-2 0-3.176-9.66-1.391-9.66-7.781 0-3.356 2.909-5.462 6.572-5.462 2.945 0 5.387 1.357 6.644 3.713l-3.268 1.82c-.647-1.392-1.904-2.035-3.376-2.035-1.401 0-2.622.607-2.622 1.892zm16.556 0c0 3.249 9.66 1.285 9.66 7.89 0 3.57-3.124 5.497-7.003 5.497-3.591 0-6.176-1.607-7.326-4.177l3.34-1.927c.575 1.606 2.011 2.57 3.986 2.57 1.724 0 3.053-.571 3.053-2 0-3.176-9.66-1.391-9.66-7.781 0-3.356 2.908-5.462 6.572-5.462 2.944 0 5.386 1.357 6.643 3.713l-3.268 1.82c-.646-1.392-1.903-2.035-3.375-2.035-1.401 0-2.622.607-2.622 1.892z" fill="currentColor"></path></svg>
        </a>
    </h1>
  </header>
  <main class="w-full bg-gray-200">
    <div class="flex flex-col md:flex-row gap-5 mx-auto max-w-7xl py-6 sm:px-6 lg:px-8">
      <!--Content-->
      <div class="w-full bg-white card">
        <scoreboard />
        <TabGroup>
          <TabList class="card flex justify-evenly items-center font-source font-bold">
            <Tab  as="template" v-slot="{selected}"
                  v-for="tab in tabs" :key="tab.name"
                  >
                  <button
                      :class="[
                        tab.class,
                        selected
                          ? 'bg-white shadow  text-red-800 border-b-2 border-red-800' :
                          ''
                      ]"
                    >
                      {{ tab.name }}
                  </button>
            </Tab>
            
          </TabList>
          </TabGroup>
        <pitch :teams="teams"/>
        <team-startup :teams="teams"/>
      </div>
      <!--SideBar-->
      <div class="w-full md:w-80 bg-white card">
        <h1>SideBar</h1>
      </div>
    </div>
  </main>
</template>
