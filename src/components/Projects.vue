<template>
  <section id="projects">
		<h2	class="display-2 font-weight-bold mb-6 text-center">{{content.metadata.title}}</h2>
    <h3 class="display-1 font-weight-bold mb-6 text-center">{{content.metadata.description}}</h3>
    <v-row justify="center">
			<v-col cols="10">
        <v-card v-for="(post, index) in content.metadata.items" :key="index" color="transparent">
          <v-card-title>{{post.title}}</v-card-title>
          <v-card-subtitle>{{post.content}} Date : {{post.date}}</v-card-subtitle>
          <v-card-text>{{post.tag}} : {{post.link}}</v-card-text>
          <v-img :src="getImgUrl(post.image)"></v-img>
        </v-card>
      </v-col>
    </v-row>
  </section>
</template>

<script>
export default {
  name: "Projects",
  props: ['content'],
  methods: {
    getImgUrl(img) {
      if(img == undefined || img == "")
        return ""
      return require('../assets/img/projects/'+img)
    },
  },
};
</script>