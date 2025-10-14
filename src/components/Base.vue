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
		<v-sheet rounded="lg" style="height: 80vh;" class="position-relative background-blur" elevation="10">
		    <p class="pa-4">NAVIGATION</p>
		    <v-divider thickness="4" role="presentation" color="warning" />
		    <v-list mandatory v-model:selected="selected" class="foreground-blur">
			<v-list-item v-for="item in items" :key="item.value" :title="item.title" 
			@click="selectedTab = item.value" 
			style="background-color: #c9daf8ff" :value="item.value" color="info" class="text-center ma-1" rounded="shaped" />
		    </v-list>
		    <div style="text-align: center" class="position-absolute bottom-0 right-0 left-0">
			<v-divider thickness="10" class="pb-8" color="warning" role="presentation" />
			<v-btn target="_blank" href="https://github.com/asand2113/portfolio-website" block class="background-blur">© 2025 Andrew Sand</v-btn>
		    </div>
		</v-sheet>
	    </v-col>
	    <v-col>
		<v-sheet rounded="lg" style="height: 80vh" elevation="10" class="background-blur">
		    <v-card title="WELCOME!" v-if="selectedTab === 1" class="h-100 w-100 foreground-blur" rounded="lg"> 
			<v-card-text class="pt-4 h-100 w-100 rounded-t-xl">
			    Welcome to my personal website! <br/>
			    Use the tabs on the left to navigate!
			    <svg style="position: absolute; width: 0; height: 0;">
				<filter id="liquid-distortion">
				    <feTurbulence type="fractalNoise" baseFrequency="0.05" numOctaves="2" result="turbulence" />
				    <feDisplacementMap in2="turbulence" in="SourceGraphic" scale="20" xChannelSelector="R" yChannelSelector="G" />
				    <feGaussianBlur stdDeviation="1" in="SourceGraphic" result="blurredSource" />
				    <feBlend in="blurredSource" in2="SourceGraphic" mode="multiply" />
				</filter>
			    </svg>
			    <div style="height: 10vh; display: flex; justify-content: center; align-items: center; background: url(images/Minesweeper.PNG)">
				<v-btn rounded="xl" class="background-blur">
				    Test
				</v-btn>
			    </div>
			</v-card-text>
		    </v-card>
		    <v-card title="ABOUT ME" v-if="selectedTab === 2" class="h-100 w-100" rounded="lg">
			<v-card-text style="background-color: #c9daf8ff" class="pt-4 h-100 w-100 rounded-t-xl">
			    <v-row>
				<v-col cols="3">
				    <v-img src="images/Portfolio.PNG" />
				    Temp Spot where a picture of me will go
				</v-col>
				<v-col>
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
				</v-col>
			    </v-row>
			</v-card-text>
		    </v-card>
		    <v-card title="PROJECTS" v-if="selectedTab === 3" class="h-100 w-100" rounded="lg">
			<v-card-text style="background-color: #c9daf8ff" class="pt-4 h-100 w-100 rounded-t-xl">
			    <v-row align="center" class="fill-height">
			    <v-data-iterator
			      :items="projects"
			      :items-per-page="3">

			      <template v-slot:default="{ items }">
				<v-container class="pa-2">
				  <v-row dense align="stretch">
				    <v-col
				      v-for="(item, i) in items"
				      :key="i"
				      cols="auto"
				      md="4">
				      <v-card class="pb-3 fill-height" border>
					<v-img :src="`images/${item.raw.img}`" aspect-ratio="1" cover></v-img>

					<v-list-item :subtitle="item.raw.subtitle" class="mb-8">
					  <template v-slot:title>
					    <strong class="text-h6 mb-2">{{ item.raw.title }}</strong>
					  </template>
					</v-list-item>
					<div style="text-align: center" class="ma-2 position-absolute bottom-0 right-0 left-0">
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
			    </v-row>
			</v-card-text>
		    </v-card>
		    <v-card title="CREDITS" v-if="selectedTab === 4" class="h-100 w-100" rounded="lg">
			<v-card-text style="background-color: #c9daf8ff" class="pt-4 h-100 w-100 rounded-t-xl">
			    Designed and Programmed by Andrew Sand <br/>
			    Made using Vue (With Vuetify), Vite, and TypeScript <br/>
			    <a target="_blank" href="https://github.com/asand2113/portfolio-website">Website Source Code</a>
			    <v-expansion-panels class="mt-4">
				<v-expansion-panel title="Attributions">
				    <v-expansion-panel-text>
					<ul style="list-style-type:none;">
					    <li><a target="_blank" href="https://vite.dev/">Vite</a>,
						included under the <a target="_blank" href="https://opensource.org/license/MIT">MIT License</a></li>
					    <li><a target="_blank" href="https://vuejs.org/">Vue</a>,
						included under the <a target="_blank" href="https://opensource.org/license/MIT">MIT License</a></li>
					    <li><a target="_blank" href="https://vuetifyjs.com/">Vuetify</a>,
						included under the <a target="_blank" href="https://opensource.org/license/MIT">MIT License</a></li>
					</ul> 
				    </v-expansion-panel-text>
				</v-expansion-panel>
			    </v-expansion-panels>
			</v-card-text>
		    </v-card>
		</v-sheet>
	    </v-col>
	</v-row>
    </v-container>
</template>

<style scoped>
.background-blur {
    border: 1px solid rgba(255, 255, 255, 0.75);
    background: rgba(180, 255, 248, 0.15); 
    backdrop-filter: blur(2px) saturate(150%); 
    box-shadow: 0 8px 32px rgba(31, 38, 135, 0.2); 
    color: white; 
}

.v-btn.background-blur:hover {
    transform: translateY(-3px);
    transition: transform 0.4s ease-in-out;
}

.foreground-blur {
    color: white;
    background: rgba(255, 255, 255, 0);
}
</style>
