<template>
  <div>
    <v-navigation-drawer
      v-model="drawer"
      :clipped="$vuetify.breakpoint.lgAndUp"
      app
    >
      <v-list dense>
        <template>
          <v-list-item :to="{ name: 'AdminMain' }">
            <v-list-item-action>
              <v-icon>home</v-icon>
            </v-list-item-action>
            <v-list-item-title> Inicio </v-list-item-title>
          </v-list-item>
        </template>
        <template>
          <v-list-group>
            <v-list-item slot="activator">
              <v-list-item-content>
                <v-list-item-title> Almacen </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item :to="{ name: 'Stock' }">
              <v-list-item-action>
                <v-icon>mdi-store-24-hour</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title> Stock </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item :to="{ name: 'Product' }">
              <v-list-item-action>
                <v-icon>mdi-clipboard-edit-outline</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title> Articulos </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item :to="{ name: 'Category' }">
              <v-list-item-action>
                <v-icon>mdi-view-dashboard</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title> Categorias </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </template>
        <template>
          <v-list-group>
            <v-list-item slot="activator">
              <v-list-item-content>
                <v-list-item-title> Ventas </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item :to="{ name: 'Sell' }">
              <v-list-item-action>
                <v-icon>mdi-piggy-bank</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title> Ventas </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item :to="{ name: 'Client' }">
              <v-list-item-action>
                <v-icon>mdi-account-group</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title> Clientes </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group> </template
        ><template>
          <v-list-group>
            <v-list-item slot="activator">
              <v-list-item-content>
                <v-list-item-title> Accesos </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item :to="{ name: 'User' }">
              <v-list-item-action>
                <v-icon>mdi-account</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title> Usuario </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <div>
              <v-list-item :to="{ name: 'Sell' }">
                <v-list-item-action>
                  <v-icon>mdi-piggy-bank</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                  <v-list-item-title> Ventas </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </div>
          </v-list-group>
        </template>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="$vuetify.breakpoint.lgAndUp"
      app
      color="blue darken-3"
      dark
    >
      <v-toolbar-title style="width: 300px" class="ml-0 pl-3">
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <span class="hidden-sm-and-down">Administración</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <div v-if="!this.$vuetify.theme.dark">
        <v-btn @click="darkThemeSwitch" icon>
          <v-icon>mdi-lightbulb-off</v-icon>
        </v-btn>
      </div>
      <div v-else>
        <v-btn @click="darkThemeSwitch" icon>
          <v-icon>mdi-lightbulb-on</v-icon>
        </v-btn>
      </div>
      <v-btn @click="logOut" icon>
        <v-icon>logout</v-icon>
      </v-btn>
    </v-app-bar>
  </div>
</template>
<script>
export default {
  name: "AdminNavigator",
  data() {
    return {
      drawer: true,
    };
  },
  methods: {
    darkThemeSwitch() {
      let theme = localStorage.getItem("theme");
      if (theme != "dark") {
        localStorage.setItem("theme", "dark");
        this.$vuetify.theme.dark = true;
      } else {
        localStorage.removeItem("theme");
        this.$vuetify.theme.dark = false;
      }
    },
    logOut() {
      this.$store.dispatch("close");
      this.$router.push({ name: "Login" });
    },
  },
};
</script>
<style lang="css"></style>
