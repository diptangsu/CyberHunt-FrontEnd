<template>
  <v-app id="inspire" dark>
    <v-navigation-drawer v-model="sideNav" clipped left-fixed-navbar app>
      <v-list dense>
        <v-list-tile v-for="item in menuItems1" :key="item.title" router :to="item.link">
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile v-if="userIsAuthenticated" @click="onLogout">
          <v-list-tile-action>
            <v-icon>exit_to_app</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>Logout</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar app fixed clipped-left>
      <v-toolbar-side-icon @click.stop="sideNav = !sideNav"></v-toolbar-side-icon>
      <v-toolbar-title>
        <router-link to="/" tag="span" style="cursor:pointer">DevMeet</router-link>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-xs-only">
        <v-btn flat v-for="item in menuItems2" :key="item.title" router :to="item.link">
          <v-icon left>{{ item.icon }}</v-icon>
          {{ item.title }}
        </v-btn>
        <v-btn flat v-if="userIsAuthenticated" @click="onLogout">
          <v-icon left>exit_to_app</v-icon>Logout
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      sideNav: true,
      menuItems1: [
        { icon: "face", title: "One", link: "/signup" },
        { icon: "lock_open", title: "Two", link: "/signin" },
        { icon: "lock_open", title: "Two", link: "/signin" },
        { icon: "lock_open", title: "Two", link: "/signin" },
        { icon: "lock_open", title: "Two", link: "/signin" },
        { icon: "lock_open", title: "Two", link: "/signin" },
        { icon: "lock_open", title: "Three", link: "/signin" },
        { icon: "lock_open", title: "Three", link: "/signin" },
        { icon: "lock_open", title: "Three", link: "/signin" },
        { icon: "lock_open", title: "Three", link: "/signin" }
      ],
      menuItems2: [
        { icon: "face", title: "Sign up", link: "/signup" },
        { icon: "lock_open", title: "Sign in", link: "/signin" }
      ]
    };
  }
};
</script>