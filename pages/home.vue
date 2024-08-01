<template>
    <v-responsive class="border rounded" >
        <v-app>
            <v-app-bar :elevation="2" style="background-color: #694F8E;">
                <template v-slot:prepend>
                </template>

                <!-- <v-app-bar-title> email:{{ email }}  username={{ username }}</v-app-bar-title> -->
                <div class="text-center" style="color: #F5EDED;">
                    {{ email }}
                    <v-btn prepend-icon="mdi-check-circle" @click="logout">
                        <template v-slot:prepend>
                            <v-icon color="success"></v-icon>
                        </template>
                        Logout
                    </v-btn>
                </div>
            </v-app-bar>



            <v-main style="background-color: #F5EDED; ">
                <v-container>
                    <v-carousel>
                        <v-carousel-item src="https://cdn.vuetifyjs.com/images/cards/docks.jpg" cover></v-carousel-item>

                        <v-carousel-item src="https://cdn.vuetifyjs.com/images/cards/hotel.jpg" cover></v-carousel-item>

                        <v-carousel-item src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
                            cover></v-carousel-item>
                    </v-carousel>
                    <h1>Main Content</h1> <v-row>
                        <v-col v-for="n in 9" :key="n" class="d-flex child-flex" cols="4">
                            <v-img :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
                                :src="`https://picsum.photos/500/300?image=${n * 5 + 10}`" aspect-ratio="1"
                                class="bg-grey-lighten-2" cover>
                                <template v-slot:placeholder>
                                    <v-row align="center" class="fill-height ma-0" justify="center">
                                        <v-progress-circular color="grey-lighten-5" indeterminate></v-progress-circular>
                                    </v-row>
                                </template>
                            </v-img>
                        </v-col>
                    </v-row>
                </v-container>
            </v-main>
        </v-app>
    </v-responsive>

     <!-- Footer -->
  <MDBFooter :text="['center', 'lg-start', 'muted']">
    <!-- Section: Social media -->
    <section
      class="d-flex justify-content-center justify-content-lg-between p-4 border-bottom"
    >
      <!-- Left -->
      <div class="me-5 d-none d-lg-block">
        <span>Get connected with us on social networks:</span>
      </div>
      <!-- Left -->

      <!-- Right -->
      <div>
        <a href="" class="me-4 text-reset">
          <MDBIcon
            class="link-secondary"
            iconStyle="fab"
            icon="facebook-f"
          ></MDBIcon>
        </a>
        <a href="" class="me-4 text-reset">
          <MDBIcon
            class="link-secondary"
            iconStyle="fab"
            icon="twitter"
          ></MDBIcon>
        </a>
        <a href="" class="me-4 text-reset">
          <MDBIcon
            class="link-secondary"
            iconStyle="fab"
            icon="google"
          ></MDBIcon>
        </a>
        <a href="" class="me-4 text-reset">
          <MDBIcon
            class="link-secondary"
            iconStyle="fab"
            icon="instagram"
          ></MDBIcon>
        </a>
        <a href="" class="me-4 text-reset">
          <MDBIcon
            class="link-secondary"
            iconStyle="fab"
            icon="linkedin"
          ></MDBIcon>
        </a>
        <a href="" class="me-4 text-reset">
          <MDBIcon
            class="link-secondary"
            iconStyle="fab"
            icon="github"
          ></MDBIcon>
        </a>
      </div>
      <!-- Right -->
    </section>
    <!-- Section: Social media -->

    <!-- Section: Links  -->
    <section class="">
      <MDBContainer class="text-center text-md-start mt-5">
        <!-- Grid row -->
        <MDBRow class="mt-3">
          <!-- Grid column -->
          <MDBCol md="3" lg="4" xl="3" class="mx-auto mb-4">
            <!-- Content -->
            <h6 class="text-uppercase fw-bold mb-4">
              <i class="fas fa-gem me-3 link-secondary"></i>Company name
            </h6>
            <p>
              Here you can use rows and columns to organize your footer
              content. Lorem ipsum dolor sit amet, consectetur
              adipisicing elit.
            </p>
          </MDBCol>
          <!-- Grid column -->

          <!-- Grid column -->
          <MDBCol md="2" lg="2" xl="2" class="mx-auto mb-4">
            <!-- Links -->
            <h6 class="text-uppercase fw-bold mb-4">Products</h6>
            <p>
              <a href="#!" class="text-reset">Angular</a>
            </p>
            <p>
              <a href="#!" class="text-reset">React</a>
            </p>
            <p>
              <a href="#!" class="text-reset">Vue</a>
            </p>
            <p>
              <a href="#!" class="text-reset">Laravel</a>
            </p>
          </MDBCol>
          <!-- Grid column -->

          <!-- Grid column -->
          <MDBCol md="3" lg="2" xl="2" class="mx-auto mb-4">
            <!-- Links -->
            <h6 class="text-uppercase fw-bold mb-4">Useful links</h6>
            <p>
              <a href="#!" class="text-reset">Pricing</a>
            </p>
            <p>
              <a href="#!" class="text-reset">Settings</a>
            </p>
            <p>
              <a href="#!" class="text-reset">Orders</a>
            </p>
            <p>
              <a href="#!" class="text-reset">Help</a>
            </p>
          </MDBCol>
          <!-- Grid column -->

          <!-- Grid column -->
          <MDBCol md="4" lg="3" xl="3" class="mx-auto mb-md-0 mb-4">
            <!-- Links -->
            <h6 class="text-uppercase fw-bold mb-4">Contact</h6>
            <p>
              <i class="fas fa-home me-3 link-secondary"></i> New York,
              NY 10012, US
            </p>
            <p>
              <i class="fas fa-envelope me-3 link-secondary"></i>
              info@example.com
            </p>
            <p>
              <MDBIcon icon="phone" class="me-3 link-secondary" />
              + 01 234 567 88
            </p>
            <p>
              <MDBIcon icon="print" class="me-3 link-secondary" />
              + 01 234 567 89
            </p>
          </MDBCol>
          <!-- Grid column -->
        </MDBRow>
        <!-- Grid row -->
      </MDBContainer>
    </section>
    <!-- Section: Links  -->

    <!-- Copyright -->
    <div
      class="text-center p-4"
      style="background-color: rgba(0, 0, 0, 0.05)"
    >
      © 2021 Copyright:
      <a class="text-reset fw-bold" href="https://mdbootstrap.com/"
        >MDBootstrap.com</a
      >
    </div>
    <!-- Copyright -->
  </MDBFooter>
  <!-- Footer -->
</template>

<script>
import axios from "axios";
export default {
  data: () => ({
      id: '',
      username: '',
      email: '',
      status: '',
      passwd: '',
      picture: '',
  }),
  async mounted() {
    let user = window.sessionStorage.getItem("email");
    console.log("user=", user);
   const response = await axios.get("http://localhost:7000/listid?email="+ user);
   let data = response.data;
   console.log('user=',data.row.username)
   this.email=data.row.email
   this.username=data.row.username
  },
  methods: {
    logout() {
      window.sessionStorage.clear();
      this.$router.replace("/login");
    },
  },
 };
</script>