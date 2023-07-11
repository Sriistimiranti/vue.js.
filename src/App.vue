<template>
  <v-app>

    <v-app-bar app color="primary" dark extended>
      <v-menu transition="slide-y-transition"></v-menu>

  <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

  <v-toolbar-title>Vueshop_Mira</v-toolbar-title>

  <!-- pemisah konten -->
  <v-spacer></v-spacer>

  <v-btn icon to="/about">
    <v-badge color="orange" overlap>
      <template v-slot:badge>
        <span>3</span>
      </template>
      <v-icon>mdi-cart</v-icon>
    </v-badge>
  </v-btn>

  <v-text-field
  slot="extension" 
  hide-details
  append-icon="mdi-microphone"
  flat
  label="Search"
  prepend-inner-icon="mdi-magnify"
  solo-inverted
></v-text-field>

</v-app-bar>

<v-card>
  <v-navigation-drawer app  v-model="drawer">
    
    <v-list-item v-if="!guest">
  <v-list-item-avatar>
    <v-img src="https://th.bing.com/th/id/OIP.1YiSHIwwY0lk2eOqUoAZ4wHaLH?pid=ImgDet&rs=1"></v-img>
  </v-list-item-avatar>
  <v-list-item-content>
    <v-list-item-title>Mira</v-list-item-title>
  </v-list-item-content>
</v-list-item>

<template v-slot:append v-if="!guest">
  <div class="pa-2">
    <v-btn block color="red" dark>
      <v-icon left>mdi-lock</v-icon>
        Logout
    </v-btn>
  </div>
</template>

<v-divider></v-divider>
    <v-list>
          <div class="pa-2" v-if="guest">
      <v-btn block color="primary" class="mb-1">
        <v-icon left>mdi-lock</v-icon>
          Login
      </v-btn>
      <v-btn block color="success">
        <v-icon left>mdi-account</v-icon>
          Register
      </v-btn>
    </div>

      <v-list-item
        v-for="(item, index) in menus"
        :key="`menu-`+index"
        :to="item.route"
      >
        <v-list-item-icon>
          <v-icon left>{{ item.icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</v-card>

    <v-content>
      <v-container fluid>
        <!-- jika menggunakan vue-router -->
        <router-view></router-view>
      </v-container>
    </v-content>

    <v-card>
      <v-footer absolute app>
        <v-card-text class="text-center">
          &copy; {{ new Date().getFullYear() }} — <strong>Vueshop_Mira</strong>
        </v-card-text>
      </v-footer>
    </v-card>

  </v-app>
</template>
<script>
export default {
  name: 'App',
  data: () => ({
  drawer: false,
  menus: [
    { title: 'Home', icon: 'mdi-home', route: '/' },
    { title: 'About', icon: 'mdi-account', route: '/about' },
  ],
  guest: false
})
};
</script>