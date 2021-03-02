<template>
  <section id="skills">
    <h2 class="display-2 font-weight-bold mb-6 text-center">{{content.metadata.title}}</h2>
    <v-row>
      <v-col md="2" sm="4" v-for="(post, index) in this.content.metadata.items" :key="index">
        <v-card flat color="transparent">
          <v-img max-height="100" contain id="imgLogo" class="img-responsive mx-auto d-block" :src="getImgUrl(post.img)" :alt="post.title"/>
          <v-card-text id="divAlt" class="altCaption text-center">{{post.title}}</v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </section>
</template>

<script>
    export default {
        name: 'Skills',
        props: ['content'],
        methods: {
            getImgUrl(img) {
                return require('../assets/img/logo/'+img);
            },
        },
    }
</script>