<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <!-- news api && key -->
      <!-- http://newsapi.org/v2/top-headlines?country=us&apiKey=eca7122ea72240c6bef1aaf6f5e90e97 -->
      <v-row justify="center" class="text-center">
        <v-col cols="10">
          <vuetify-logo />
          <!-- card -->
          <v-card class="rounded-lg my-7 mx-auto" v-for="(item, index) in articles" :key="index">
            <div v-if="item.urlToImage">
              <v-card-title>
                <img class="rounded-lg" :src="item.urlToImage" alt="item.source.name" width="100%">
                <span class="mt-2 ml-2">{{ item.source.name }}</span>
              </v-card-title>
              <v-card-subtitle>
                {{ item.title }}
              </v-card-subtitle>
              <v-card-text>
                {{ item.content }}
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn class="rounded-lg" :href="item.url" target="_blank" block>
                  More
                </v-btn>
              </v-card-actions>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-flex>
  </v-layout>
</template>

<script>
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  components: {
    VuetifyLogo
  },

  async asyncData({app}){
    const {articles} = await app.$axios.$get('http://newsapi.org/v2/top-headlines?country=us&apiKey=eca7122ea72240c6bef1aaf6f5e90e97');
    return {articles};
  }
}
</script>
