<script setup lang="ts">
    import { shallowRef } from 'vue'
    import { ref } from 'vue'
    import { mdiArrowLeft } from '@mdi/js'
    import { mdiArrowRight } from '@mdi/js'

    const selected = shallowRef([1]);
    const selectedTab = ref(1);
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
  ];
    const projects = [
    {
      img: 'Portfolio.PNG',
      title: 'Portfolio Website',
      subtitle: 'The website you are viewing now! A portfolio website made using Vue, Vite, and Vuetify.',
      link: 'https://github.com/asand2113/portfolio-website',
    },
    {
      img: 'YT-Controller.PNG',
      title: 'yt-download-controller',
      subtitle: 'A CLI tool to make using yt-dlp a breeze.',
      link: 'https://github.com/asand2113/yt-download-controller',
    },
    {
      img: 'Minesweeper.PNG',
      title: 'Minesweeper C++',
      subtitle: 'A simple terminal-based clone of Minesweeper made using C++.',
      link: 'https://github.com/asand2113/minesweeper-cpp',
    },
  ];

</script>

<template>
    <v-container class="h-screen">
	<v-row class="fill-height mx-auto" align="center" style="max-width: 75%">
	    <v-col cols="3" xl="2" xxl="2">
		<v-sheet border="primary lg" rounded="lg" style="height: 80vh; background: rgba(255, 255, 255, 0.5)" class="position-relative" elevation="10">
		    <p class="pa-4">NAVIGATION</p>
		    <v-divider thickness="4" role="presentation" />
		    <v-list mandatory v-model:selected="selected">
			<v-list-item v-for="item in items" :key="item.value" :title="item.title" 
			@click="selectedTab = item.value" 
			style="background-color: #c9daf8ff" :value="item.value" color="info" class="text-center ma-1" rounded="shaped" />
		    </v-list>
		    <div style="text-align: center" class="position-absolute bottom-0 right-0 left-0">
			<a target="_blank" href="https://github.com/asand2113/portfolio-website">© 2025 Andrew Sand</a>
		    </div>
		</v-sheet>
	    </v-col>
	    <v-col>
		<v-sheet border="primary lg" rounded="lg" style="height: 80vh" elevation="10">
		    <v-card title="WELCOME!" v-if="selectedTab === 1" class="h-100 w-100" rounded="lg"> 
			<v-card-text style="background-color: #c9daf8ff" class="pt-4 h-100 w-100 rounded-t-xl">
			    Welcome to my personal website! <br/>
			    Use the tabs on the left to navigate!
			</v-card-text>
		    </v-card>
		    <v-card title="ABOUT ME" v-if="selectedTab === 2" class="h-100 w-100" rounded="lg">
			<v-card-text style="background-color: #c9daf8ff" class="pt-4 h-100 w-100 rounded-t-xl">
			    <v-card>
				<v-card-title>
				    Andrew Sand
				</v-card-title>
				<v-card-subtitle>
				    Software Engineer
				</v-card-subtitle>
				<v-card-text>
				    Education:<br/>
				    Bachelor of Science in Software Engineering from Iowa State University.<br/>
				    Minored in Music Technology.
				</v-card-text>
			    </v-card>
			</v-card-text>
		    </v-card>
		    <v-card title="PROJECTS" v-if="selectedTab === 3" class="h-100 w-100" rounded="lg">
			<v-card-text style="background-color: #c9daf8ff" class="pt-4 h-100 w-100 rounded-t-xl">
			    <v-data-iterator
			      :items="projects"
			      :items-per-page="3">

			      <template v-slot:default="{ items }">
				<v-container class="pa-2" fluid>
				  <v-row dense>
				    <v-col
				      v-for="item in items"
				      :key="item.title"
				      cols="auto"
				      md="4">
				      <v-card class="pb-3" border flat>
					<v-img :src="`images/${item.raw.img}`"></v-img>

					<v-list-item :subtitle="item.raw.subtitle" class="mb-2">
					  <template v-slot:title>
					    <strong class="text-h6 mb-2">{{ item.raw.title }}</strong>
					  </template>
					</v-list-item>
					<div class="ma-2">
					    <v-btn :href="item.raw.link" target="_blank" block color="primary">Go to Project</v-btn>
					</div>

				      </v-card>
				    </v-col>
				  </v-row>
				</v-container>
			      </template>

			      <template v-slot:footer="{ page, pageCount, prevPage, nextPage }">
				<div class="d-flex align-center justify-center pa-4">
				  <v-btn
				    :disabled="page === 1"
				    density="comfortable"
				    :icon="mdiArrowLeft"
				    variant="tonal"
				    rounded
				    @click="prevPage"
				  ></v-btn>

				  <div class="mx-2 text-caption">
				    Page {{ page }} of {{ pageCount }}
				  </div>

				  <v-btn
				    :disabled="page >= pageCount"
				    density="comfortable"
				    :icon="mdiArrowRight"
				    variant="tonal"
				    rounded
				    @click="nextPage"
				  ></v-btn>
				</div>
			      </template>
			    </v-data-iterator>
			</v-card-text>
		    </v-card>
		    <v-card title="CREDITS" v-if="selectedTab === 4" class="h-100 w-100" rounded="lg">
			<v-card-text style="background-color: #c9daf8ff" class="pt-4 h-100 w-100 rounded-t-xl">
			    Designed and Programmed by Andrew Sand <br/>
			    Made using Vue (With Vuetify), Vite, and TypeScript <br/>
			    <a target="_blank" href="https://github.com/asand2113/portfolio-website">Website Source Code</a>
			</v-card-text>
		    </v-card>
		</v-sheet>
	    </v-col>
	</v-row>
    </v-container>
</template>

<style scoped>
</style>
