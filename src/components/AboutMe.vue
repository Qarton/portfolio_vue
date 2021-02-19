<template>
  <section id="about-me">
        <div class="py-12"></div>

        <v-container class="text-center">
          <h2 class="display-2 font-weight-bold mb-3">ABOUT ME</h2>

          <v-responsive
            class="mx-auto mb-8"
            width="56"
          >
            <v-divider class="mb-1"></v-divider>

            <v-divider></v-divider>
          </v-responsive>

          <v-avatar
            class="elevation-12 mb-12"
            size="128"
          >
            <v-img src="../assets/img/Math.jpg"></v-img>
          </v-avatar>

          <v-row>
            <v-col>
            {{content.metadata.pres_first}}
            </v-col>

            <v-col>
              <h3>{{ user.name }}</h3>
              <div class="data"><strong>E-mail:</strong> {{ user.email }}</div>
              <div class="data"><strong>Phone:</strong> {{ user.phone }}</div>
              <div class="data"><strong>City:</strong> {{ user.city }}</div>
              <div class="data"><strong>Languages:</strong> {{ user.lang }}</div>
            </v-col>


          </v-row>

        </v-container>

        <div class="py-12"></div>
      </section>
</template>

<script>
export default {
  name: 'AboutMe',
  props: ['user', 'content']
}
</script>
