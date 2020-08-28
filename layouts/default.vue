<template>
  <v-app dark>
    <v-navigation-drawer v-model="drawer" :clipped="clipped" fixed :app="navBar">

      <v-list>
        <v-list-item v-for="(item, i) in items" :key="i" :to="item.to" router exact >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>

    </v-navigation-drawer>

    <!-- Nav Bar -->
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer; navBar = !navBar"/>
      <v-toolbar-title v-text="title" />
    </v-app-bar>

    <!-- Pages goes here -->
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

  </v-app>
</template>

<script>
export default {
  data () {
    return {
      navBar: false,
      drawer: false,
      clipped: true,

      items: [
        {
          icon: 'mdi-home',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'About',
          to: '/about'
        }
      ],

      title: 'News App'
    }
  }
}
</script>
