<template>
  <nav>
    <v-toolbar color="grey lighten-3" app flat>
      <v-app-bar-nav-icon   @click="drawer = !drawer" app ></v-app-bar-nav-icon>
      <v-toolbar-title class="text-uppercase green--text">
        <span class="font-weight-black">todo</span>
        <span class="">Ninja</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn color="grey" flat depressed>
        <span>Sign out</span>
        <v-icon right>mdi-logout</v-icon>
      </v-btn>
    </v-toolbar>
    <v-navigation-drawer class=" purple lighten-1 " app  v-model="drawer" temporary c>
      <v-list dark>
        <v-list-item
            v-for="item in items"
            :key="item.text"
            router :to="item.link"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

    </v-navigation-drawer>
  </nav>
</template>

<script>
export default {
  name: 'toolbar',
  data() {
    return {
      'drawer': 'true',
      'items':[
        {'title':'Dashboard'  ,'icon':'mdi-view-dashboard' ,'link':'/'},
        {'title':'Team'       ,'icon':'mdi-account-multiple'      ,'link':'/Teams'},
        {'title':'My Projects','icon':'mdi-folder'    ,'link':'/Projects'},
      ]
    }
  }
}
</script>
