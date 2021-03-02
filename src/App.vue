<template>
  <v-app>
    <v-main v-if="isLoaded">
      <landing-page :msg="user.name"/>
      <div class="py-16"></div>
      <about-me :user="user" :content="findSlug('description')" />
      <div class="py-16"></div>
      <experience :content="findSlug('experiences')" />
      <div class="py-12"></div>
      <skills :content="findSlug('skills')" />
      <div class="py-12"></div>
      <projects :content="findSlug('projects')" />
    </v-main>
  </v-app>
</template>

<script>
import LandingPage from './components/LandingPage'
import AboutMe from './components/AboutMe'
import Experience from './components/Experience'
import Skills from './components/Skills.vue'
import Projects from './components/Projects.vue'

import { bucket } from "./cosmic.js"


export default {
  name: "App",
  components: {
    LandingPage,
    AboutMe,
    Experience,
    Skills,
    Projects
  },
  data: () => ({
    isLoaded: false,
    user: {},
    posts: [],
  }),
  methods: {
    fetchPosts() {
      return bucket.getObjects({
        type: "portfolio-contents",
        props: "slug,title,metadata",
      });
    },
    fetchUser() {
      return bucket.getObjects({
        type: "portfolio-contents",
        q: "user-data",
        props: "slug,title,metadata",
      });
    },
    fetchObjectTypes() {
      return bucket.getObjectTypes();
    },
    findSlug(slug) {
      return this.posts.find((item) => {
        return item.slug === slug;
      });
    },
    extractFirstObject(objects) {
      if(objects.objects == null)
        return void 0;
      else
        return objects.objects[0];
    }
  },
  created() {
    document.body.classList.add("loading");
    Promise.all([this.fetchPosts(), this.fetchUser()]).then(([posts, user_data]) => {
      user_data = this.extractFirstObject(user_data);
      this.posts = posts.objects;
      this.user = {
        name: user_data.metadata.name,
        status: user_data.metadata.status,
        email: user_data.metadata.email,
        phone: user_data.metadata.phone,
        city: user_data.metadata.city,
        lang: user_data.metadata.lang,
        photo: user_data.metadata.photo,
      }
      this.isLoaded = true;
      this.$nextTick(() => document.body.classList.remove("loading"));
    });
  },
};
</script>
