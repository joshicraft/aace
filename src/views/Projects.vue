<template>
  <v-container fill-height>
    <v-layout justify-center align-center>
      <v-flex xs8 class="mb-5">
        <alpha-gallery
          :categories="categories"
          :projects="projects"
        />
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  export default {
    metaInfo: {
      title: 'Projects of Anderson Air Conditioning & Electrical',
      meta: [
        { name: 'description', content: "Here's but a few of the Electrical and Air Conditioning projects we've worked on" }
      ]
    },
    computed: {
      categories () {
        return this.bakedViews.Projects.categories
      },
      projects () {
          return this.bakedViews.Projects.projects
      }
    }
  }
</script>
