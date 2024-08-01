<template>
  <v-app >
    <v-card 
    color="grey"
    >
      <v-layout>
       
        ///
        <v-system-bar color="light-blue darken-1" >
          <v-icon class="ms-2" icon="mdi-wifi-strength-4 " color="green darken-1"></v-icon>
        <v-icon class="ms-2" icon="mdi-signal-cellular-outline"></v-icon>
          <v-icon class="ms-2" icon="mdi-battery"></v-icon>
          <span class="ms-2">12:30</span>
        </v-system-bar>
        ///
        <v-app-bar
          :elevation="22" 
          color="deep-purple darken-3"
          gradient="to top right, rgba(19,84,122,.8), rgba(128,208,199,.8)"
        >

          <template v-slot:prepend>
            <v-app-bar-nav-icon></v-app-bar-nav-icon>
          </template>
          <v-app-bar-title>Title</v-app-bar-title>
          <v-spacer></v-spacer>
          <v-btn icon>
            <v-icon>mdi-magnify</v-icon>
          </v-btn>
          <v-btn icon >
            
            <v-icon @click="about">mdi-account</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </v-app-bar>
        <v-navigation-drawer
          class="bg-deep-purple"
          theme="dark"
          permanent
          expand-on-hover
          rail
          @click="rail = false"
        >
          <v-list-item
            prepend-avatar="\assets\images\pexels-eberhardgross-691668.jpg"
            title="Thanawat panthong"
            nav
          >
            <template v-slot:append>
              <v-btn
                icon="mdi-chevron-left"
                variant="text"
                @click.stop="rail = !rail"
              ></v-btn>
            </template>
          </v-list-item>
          <v-divider></v-divider>
          <v-list density="compact" nav>
            <v-list-item
              prepend-icon="mdi-home-city"
              title="หน้าหลัก"
              value="home"
              @click="main"
            ></v-list-item>
            <v-list-item
           
              prepend-icon="mdi-plus"
              size="x-large"
              title="เพิ่มข้อมูล"
              value="add"
              @click="add"
            ></v-list-item>
            <v-list-item
              prepend-icon="mdi-home-city"
              title="แสดงข้อมูล"
              value="home"
              @click="listdata"
            ></v-list-item>
            <v-list-item
              prepend-icon="mdi-account"
              title="เกี่ยวกับ"
              value="account"
              @click="about"
            ></v-list-item>
            <v-list-item
              prepend-icon="mdi-close-circle"
              title="LOGOUT"
              value="users"
              @click="logOut"
            ></v-list-item>
          </v-list>
        </v-navigation-drawer>
        <!-- <v-main style="height: 650px"></v-main> -->
        <v-main  
         color=""
         style="background-color: #d09dea;"
        >
         <NuxtPage ></NuxtPage>
          <!-- Main Content -->
        </v-main>
        <!--  -->

        <v-bottom-navigation v-model="value" :bg-color="color" mode="shift">
          <v-btn>
            <v-icon>mdi-television-play</v-icon>

            <span>Video</span>
          </v-btn>

          <v-btn>
            <v-icon>mdi-music-note</v-icon>

            <span>Music</span>
          </v-btn>

          <v-btn>
            <v-icon>mdi-book</v-icon>

            <span>Book</span>
          </v-btn>

          <v-btn>
            <v-icon>mdi-image</v-icon>

            <span>Image</span>
          </v-btn>
        </v-bottom-navigation>
      </v-layout>
    </v-card>
  </v-app>
</template>
<script>
import axios from 'axios'
export default {
  data() {
    return {
      drawer: true,
      rail: true,
      username: '',
      email: ''
    };
  },
  methods: {
    main(){
      this.$router.replace("/home");
    },
    listdata(){
      this.$router.replace("/listdata");
    },
    showdata(){
      this.$router.replace("/");
    },
    about(){
      this.$router.replace("/aboute");
    },
    add(){
      this.$router.replace("/add");
    },
    logOut() {
      window.sessionStorage.clear();
      this.$router.replace("/login");
    },
  },

  async mounted() {
        let user = window.sessionStorage.getItem('email')
        console.log('users=', user)
        if (!user) {
            this.$router.replace('/login')
            return
        } 
       
    },
  
};

</script>
  