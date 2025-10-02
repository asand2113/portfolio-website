<script setup lang="ts">
    import { mdiAlertCircle } from '@mdi/js'
    import { mdiGithub } from '@mdi/js'
</script>

<template>
    <v-container class="h-screen">
	<v-row align="center" class="fill-height">
	    <v-col>
		<v-sheet border="primary lg" rounded="lg">
		    <v-alert text="Welcome to my portfolio website! Unfortunately, 
			I do not have a mobile version working yet, so you will need
			to use a desktop web browser to access it. A mobile version is 
			on the way, but these things take time. :)" 
			title="Welcome to my website! However..."
			:icon="mdiAlertCircle" border="start"
			border-color="warning">
			<template v-slot:prepend>
			    <v-icon color="error"/>
			</template>
		    </v-alert>
		    <div class="d-flex justify-center">
			<v-btn class="ma-4 text-decoration-underline" target="_blank" 
			    href="https://github.com/asand2113/portfolio-website"
			    :prepend-icon="mdiGithub" color="info"
			    rounded="xl">© 2025 Andrew Sand</v-btn>
		    </div>
		</v-sheet>
	    </v-col>
	</v-row>
    </v-container>
</template>

<style scoped>
</style>
