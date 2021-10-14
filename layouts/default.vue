<template>
<v-app dark>
  <v-navigation-drawer
    v-model="drawer"
    app>
    <!-- -->
  </v-navigation-drawer>

  <v-navigation-drawer
    v-model="drawer"
    app>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            YouTube
          </v-list-item-title>
          <v-list-item-subtitle>

          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
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
    </v-navigation-drawer>

  <v-app-bar app>

    <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
    <v-toolbar-title> </v-toolbar-title>



      <v-row >
        <v-col>
          <v-toolbar dense floating class="d-flex justify-center">

          <v-text-field
            hide-details
            single-line
            prepend-icon="mdi-magnify"
          ></v-text-field>

          <v-btn icon>
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>

        </v-toolbar>
        </v-col>
      </v-row>



    <!-- -->
  </v-app-bar>

  <v-main>
      <v-container>
        <v-row>
          <v-col
            v-for="n in 24"
            :key="n"
            cols="3"
          >
            <v-card height="200" class="tile">
              <img :src="getImgUrl()" class="tile-image">
              <div class="tile-info">
                <div><img :src="getAvatarUrl()" class="tile-avatar"></div>
                <div class="tile-texts">
                  <h3>{{getTileTitle()}}</h3>
                  <p>{{getAvatarName()}}</p>
                </div>
              </div>
            </v-card>
          </v-col>
        </v-row>
      </v-container>

      <v-container fluid>
      <!-- If using vue-router -->
      <Nuxt />
    </v-container>
  </v-main>


  <v-footer app>
    <!-- -->
  </v-footer>
</v-app>
</template>

<script>
import faker from "faker"

export default {
  data () {
    return {
      drawer: null,
      items: [
          { title: 'Home', icon: 'mdi-view-dashboard' },
          { title: 'Explore', icon: 'mdi-image' },
          { title: 'Subscriptions', icon: 'mdi-help-box' },
          { title: 'Library', icon: 'mdi-view-dashboard' },
          { title: 'History', icon: 'mdi-image' },
          { title: 'Your videos', icon: 'mdi-help-box' },
          { title: 'Watch later', icon: 'mdi-view-dashboard' },
          { title: 'Liked videos', icon: 'mdi-image' },
          { title: 'Youtube premium', icon: 'mdi-help-box' },
        ],
      right: null,
    }
  },
  methods:{
    getImgUrl: ()=>{
      return faker.image.nature(400, 200, true);
    },
    getAvatarUrl: ()=>{
      return faker.image.avatar();
    },
    getAvatarName: ()=>{
      return faker.name.findName();
    },
    getTileTitle: ()=>{
      return faker.lorem.sentence();
    }

  }
}
</script>

<style scoped lang="scss">
  .tile-image {
    display: block;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  .tile{
    margin-bottom: 130px;
  }
  .tile-avatar{
    border-radius: 50%;
    width: 50px;
    height: 50px;
    margin-top: 20px;
  }
  .tile-info{
    display: flex;
    align-items: center;
  }
  .tile-texts{
    padding:25px 0 0 20px;
  }
</style>
