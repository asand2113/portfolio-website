<script setup lang="ts">
import { ref } from 'vue'

const selectedTab = ref(1)
    const items = [
    {
      title: 'HOME',
      value: 1,
    },
    {
      title: 'ABOUT ME',
      value: 2,
    },
    {
      title: 'PROJECTS',
      value: 3,
    },
    {
      title: 'CREDITS',
      value: 4,
    },
  ]
</script>

<template>
    <v-container class="h-screen">
	<v-row>
	    <v-col cols="2">
		<v-sheet border rounded style="height: 80vh" class="position-relative">
		    <p class="pa-4">NAVIGATION</p>
		    <v-divider thickness="4" role="presentation" />
		    <v-list>
			<v-list-item v-for="item in items" :key="item.title" :title="item.title" @click="selectedTab = item.value" />
		    </v-list>
		    <div style="text-align: center" class="position-absolute bottom-0 right-0 left-0">
			<a target="_blank" href="https://github.com/asand2113/portfolio-website">2025 Andrew Sand</a>
		    </div>
		</v-sheet>
	    </v-col>
	    <v-col>
		<v-sheet border rounded style="height: 80vh">
		    <v-card title="WELCOME!" v-if="selectedTab === 1">
			<v-card-text>
			    Testing
			</v-card-text>
		    </v-card>
		    <v-card title="ABOUT ME" v-if="selectedTab === 2">
		    </v-card>
		    <v-card title="PROJECTS" v-if="selectedTab === 3">
		    </v-card>
		    <v-card title="CREDITS" v-if="selectedTab === 4">
		    </v-card>
		</v-sheet>
	    </v-col>
	</v-row>
    </v-container>
</template>

<style scoped>
</style>
