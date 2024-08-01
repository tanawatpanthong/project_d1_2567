<!-- <template>
    <div class="text-center">
      <div>
        <v-btn
          class="ma-2"
          color="primary"
        >
          Accept
          <v-icon
            icon="mdi-checkbox-marked-circle"
            end
          ></v-icon>
        </v-btn>
  
        <v-btn
          class="ma-2"
          color="red"
        >
          Decline
          <v-icon
            icon="mdi-cancel"
            end
          ></v-icon>
        </v-btn>
  
        <v-btn
          class="ma-2"
        >
          <v-icon
            icon="mdi-minus-circle"
            start
          ></v-icon>
          Cancel
        </v-btn>
      </div>
  
      <div>
        <v-btn
          class="ma-2"
          color="orange-darken-2"
        >
          <v-icon
            icon="mdi-arrow-left"
            start
          ></v-icon>
          Back
        </v-btn>
  
        <v-btn
          class="ma-2"
          color="purple"
          icon="mdi-wrench"
        ></v-btn>
  
        <v-btn
          class="ma-2"
          color="indigo"
          icon="mdi-cloud-upload"
        ></v-btn>
      </div>
  
      <div>
        <v-btn
          class="ma-2"
          color="blue-lighten-2"
          icon="mdi-thumb-up"
          variant="text"
        ></v-btn>
  
        <v-btn
          class="ma-2"
          color="red-lighten-2"
          icon="mdi-thumb-down"
          variant="text"
        ></v-btn>
      </div>
    </div>
  </template> -->
  <template>
    <v-card
      title="Nutrition"
      flat
    >
      <template v-slot:text>
        <v-text-field
          v-model="search"
          label="Search"
          prepend-inner-icon="mdi-magnify"
          variant="outlined"
          hide-details
          single-line
        ></v-text-field>
      </template>
  
      <v-data-table
        :headers="headers"
        :items="students"
        :search="search"
      ></v-data-table>
    </v-card>
  </template>
  <script>
import axios from 'axios'

  export default {
    data () {
      return {
        search: '',
        headers: [
          {
            align: 'start',
            key: 'id',
            sortable: false,
            title: 'id'
          },
          { key: 'username', title: 'username' },
          { key: 'password', title: 'password' },
          { key: 'email', title: 'email' },
          { key: 'picture', title: 'picture' },
          { key: 'status', title: 'status' },
        ],
        students: [
          {
            name: 'Frozen Yogurt',
            calories: 159,
            fat: 6.0,
            carbs: 24,
            protein: 4.0,
            iron: 1,
          },
          ],
      }
    },
    async created() {
    console.log('init list data');
    const response = await axios.get('http://localhost:7000/list')
    this.students = response.data.rows
  },
  }
</script>
