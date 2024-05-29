<template>

  <v-app-bar :elevation="2">
    <div class="d-flex justify-space-between w-100 px-4">
      <p>Breilan</p>

      <ul class="d-flex ga-2 ">
        <lu>Hjem</lu>
        <lu>News</lu>
        <lu>Tickets</lu>
        <lu>FQA</lu>
      </ul>

    </div>
  </v-app-bar>

  <v-container>
    <v-row>
      <v-col>
        <v-table>
          <thead>
            <tr>
              <th>Name</th>
              <th>Score</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in score" :key="item.name">
              <td>{{ item.name }}</td>
              <td>{{ item.score }}</td>
            </tr>
          </tbody>
        </v-table>
      </v-col>
      <v-col>
        <v-card class="pa-10">
          <bracket :rounds="rounds" class="w-100 h-auto">
            <template #player="{ player }">
              {{ player.name }}
            </template>
          </bracket>
        </v-card>
      </v-col>

    </v-row>
    <v-row>
      <v-col>
        <v-expansion-panels v-model="openNews">
          <v-expansion-panel title="Latest News" value="news">
            <v-expansion-panel-text class="d-flex flex-col ga-2 h-auto">
              <v-card class="w-100">
              News 1
            </v-card>
            <v-card >
              News 2
            </v-card>
            <v-card >
              News 3
            </v-card>
            </v-expansion-panel-text>
          </v-expansion-panel>
        </v-expansion-panels>
      </v-col>
    </v-row>
  </v-container>

</template>

<script setup>
//
import { ref } from "vue";
import Bracket from "vue-tournament-bracket";

const rounds = [

  {
    games: [
      {

        player1: { id: "1", name: "Competitor 1", winner: false },
        player2: { id: "4", name: "Competitor 4", winner: true },
      },
      {

        player1: { id: "5", name: "Competitor 5", winner: false },
        player2: { id: "8", name: "Competitor 8", winner: true },
      }
    ]
  },

  {
    games: [
      {
        player1: { id: "4", name: "Competitor 4", winner: false },
        player2: { id: "8", name: "Competitor 8", winner: true },
      }
    ]
  }
];

const score = [
  { name: "Competitor 1", score: 0 },
  { name: "Competitor 4", score: 1 },
  { name: "Competitor 5", score: 0 },
  { name: "Competitor 8", score: 1 }
]; 

const openNews = ref(['news']);
</script>
