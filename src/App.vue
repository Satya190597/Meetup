<template>
  <v-app>
    <v-navigation-drawer v-model="sidenav">
      <v-list-tile v-for="item in menuItems" :key="item.title" router :to="item.link">
        <v-list-tile-action>
          <v-icon>{{item.icon}}</v-icon>
        </v-list-tile-action>
        <v-list-tile-content>{{item.title}}</v-list-tile-content>
      </v-list-tile>
    </v-navigation-drawer>
    <v-toolbar fixed dark class="pink darken-4">
      <v-toolbar-side-icon @click="sidenav = !sidenav" class="hidden-sm-and-up"></v-toolbar-side-icon>
      <v-toolbar-title>
        <router-link to="/" tag="span" style="cursor: pointer">Meetup App</router-link>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-xs-only">
        <v-btn flat v-for="item in menuItems" :key="item.title" router :to="item.link">
          <v-icon left dark>{{item.icon}}</v-icon>
          {{item.title}}
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <main>
      <router-view></router-view>
    </main>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      sidenav: false,
      menuItems: [
        {icon: 'supervisor_account', title: 'View Meetups', link: '/meetups'},
        {icon: 'room', title: 'Organize Meetup', link: '/createmeetup'},
        {icon: 'person', title: 'Profile', link: '/profile'},
        {icon: 'face', title: 'Sign Up', link: '/signup'},
        {icon: 'lock_open', title: 'Sign in', link: '/signin'}
      ]}
  },
  name: 'App'
}
</script>
