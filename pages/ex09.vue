<template>
  <div>
    <!-- <h1>Hello=> {{ message }}</h1> -->
    <div>{{ upperName }}</div>
    <div>
      <ul>
        <li v-for="st in students" :key="st.email">
          <span>{{ st.id }}</span>
          <span>{{ st.username }}</span>
          <span>{{ st.email }}</span>
          <span>{{ st.status }}</span>
        </li>
      </ul>
    </div>

    <!-- <input type="text" :value="name"><br>
    <input type="text" v-model="name"><br> -->
    
    <button @click="doSave">SAVE</button>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  data() {
    return {

      name: 'World',
      // มอคอัป
      message:
        [{ code: '001', name: 'Name1' },
        { code: '002', name: 'Name2' },
        { code: '003', name: 'Name3' },
        { code: '003', name: 'Name4' },
        ],
        students:''
    }

  },
  computed: {
    upperName() { return this.name.toUpperCase() }
  },
  async created() {
    console.log('init list data');
    const response = await axios.get('http://localhost:7000/list')
    this.message = response.data
    this.students = response.data.rows
  },
  methods: {
    async doSave() {
      console.log('SAVE data');
      const response = await axios.get('http://localhost:7000/list')
      this.message = response.data

      console.log(this.message)
    },
  },
}
</script>