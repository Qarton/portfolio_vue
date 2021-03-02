<template>
  <section id="about-me">
        <v-container class="text-center">
          <h2 class="display-2 font-weight-bold mb-3">ABOUT ME</h2>

          <v-responsive
            class="mx-auto mb-8"
            width="56"
          >
            <v-divider class="mb-1"></v-divider>

            <v-divider></v-divider>
          </v-responsive>
          <v-scroll-x-reverse-transition>
            <v-avatar
              class="elevation-12 mb-12"
              size="128"
            >
              <v-img src="../assets/img/Math.jpg"></v-img>
            </v-avatar>
          </v-scroll-x-reverse-transition>

          <v-row justify="space-around">
            <v-col cols="10" md="4">
              <h3 class="mb-4">{{ content.metadata.pres_title }}</h3>
              {{content.metadata.pres_first}}
            </v-col>

            <v-col cols="10" md="4">
              <h3 class="mb-4">{{ user.name }}</h3>
              <div class="data"><strong>E-mail:</strong> {{ user.email }}</div>
              <div class="data"><strong>Phone:</strong> {{ user.phone }}</div>
              <div class="data"><strong>City:</strong> {{ user.city }}</div>
              <div class="data"><strong>Languages:</strong> {{ user.lang }}</div>
            </v-col>

          </v-row>

        </v-container>
      </section>
</template>

<script>
export default {
  name: 'AboutMe',
  props: ['user', 'content']
}
</script>
