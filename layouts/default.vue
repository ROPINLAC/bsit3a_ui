<template>
  <v-app dark>
   <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <template v-slot:append>
        <div class="pa-2">
          <v-btn block to="/" class=" blue darken-1 white--text">
            Logout
          </v-btn>
        </div>
      </template>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-spacer />
      <v-toolbar-title >{{ title }}</v-toolbar-title>
      <v-spacer />
      <v-btn
        icon
        @click.stop="rightDrawer = !rightDrawer"
      >
        <v-icon>mdi-menu</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <div>
        <v-img src="https://i0.wp.com/backgroundabstract.com/wp-content/uploads/edd/2022/02/5594016-e1656071131636.jpg?resize=150150&ssl=1" height="100vh">
        <Nuxt />
        </v-img>
      </div>
    </v-main>
    <v-navigation-drawer
      v-model="rightDrawer"
      :right="right"
      temporary
      fixed
    >
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light>
              mdi-repeat
            </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>

    </v-navigation-drawer>
    <!-- <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer> -->
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      clipped: false,
      drawer: true,
      fixed: false,
      items: [
        {
          icon: 'mdi-view-dashboard',
          title: 'Dashboard',
          to: '/dashboard'
        },
        {
          icon: 'mdi-view-list',
          title: 'Student List',
          to: '/studentList'
        },
       
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'BSIT - 3A'
    }
  }
}
</script>