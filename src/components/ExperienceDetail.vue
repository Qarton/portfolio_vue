<template>
  <v-card>
    <v-parallax height="50" src="../assets/img/bg2.jpg">
    <v-card-title class="justify-center">{{ title }}</v-card-title>
    </v-parallax>
    <v-timeline align-top dense>
    <v-timeline-item class="resume-item" v-for="(post, index) in posts" :key="index">
      <v-card-text class="year color-darker">{{ post.year }} <strong class="color-light" v-html="post.title"></strong></v-card-text>
      <v-card-text class="color-darker" v-html="post.content"></v-card-text>
    </v-timeline-item>
    </v-timeline>
  </v-card>
</template>

<script>
export default {
  name: "Experience",
  props: ["posts", "title"],
}
</script>

<style>

</style>