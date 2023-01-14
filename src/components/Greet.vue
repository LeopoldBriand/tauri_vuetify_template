<script setup lang="ts">
import { ref } from "vue";
import { invoke } from "@tauri-apps/api/tauri";

const greetMsg = ref("");
const name = ref("");

async function greet() {
  // Learn more about Tauri commands at https://tauri.app/v1/guides/features/command
  greetMsg.value = await invoke("greet", { name: name.value });
}
</script>

<template>
  <v-card
    min-width="500"
    max-width="700"
    variant="outlined"
  >
    <v-card-item>
      <v-text-field v-model="name" label="Enter a name..." variant="underlined"></v-text-field>
      <v-btn variant="outlined" @click="greet()">Greet</v-btn>
    </v-card-item>
  </v-card>

  <p>{{ greetMsg }}</p>
</template>
