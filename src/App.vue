<template>
  <v-app id="inspire">

    <v-navigation-drawer
    v-model="drawer"
    app
    >
    <v-img
    dark
    class="pt-5 text-center blue-grey darken-1"
    >
    <v-avatar
      size="70"
      >  
        <img
          src="https://definicao.net/wp-content/uploads/2020/03/list-2389219_1280.png"
        >
      </v-avatar>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
           Lista de tarefas
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-img>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <v-container
    class="px-0"
    fluid
  >
    <v-switch
    style="margin-top:240px; margin-left:15px"
      v-model="switch1"
      :label="`Modo Escuro`"
      @click="$vuetify.theme.dark =! $vuetify.theme.dark"
    ></v-switch>
  </v-container>
    </v-navigation-drawer>

    <v-app-bar
      app
      prominent
      height="138"
      dark
     
      class="blue-grey darken-1"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
        
        ></v-img>
      </template>

      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <center>
        <v-app-bar-title
        class="mt-16"
        >
          <InputTarefa
          style="padding: 0 !important; min-width: 100% !important;"
          />

        </v-app-bar-title>
      </center>

    </v-app-bar>
    

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import InputTarefa from './components/InputTarefa.vue'
  export default {
  components: { InputTarefa },
    data: () => ({ 
      drawer: null,
      items: [
          { title: 'Tarefas', icon: 'mdi-view-dashboard', to:'/' },
          { title: 'Sobre', icon: 'mdi-help-box', to:'/sobre'  },
        ],
    }),
  }
</script>