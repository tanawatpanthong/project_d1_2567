<template>
    <v-card
      :loading="loading"
      class="mx-auto my-12"
      max-width="374"
    >
      <template slot="progress">
        <v-progress-linear
          color="deep-purple"
          height="10"
          indeterminate
        ></v-progress-linear>
      </template>
  
      <v-img
        height="250"
        src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
      ></v-img>
  
      <v-card-title>Thanawat panthong</v-card-title>
  
      <v-card-text>
        <v-row
          align="center"
          class="mx-0"
        >
          <v-rating
            :value="4.5"
            color="amber"
            dense
            half-increments
            readonly
            size="14"
          ></v-rating>
  
          <div class="grey--text ms-4">
            (tar)
          </div>
        </v-row>
  
        <div class="my-4 text-subtitle-1">
          เพศ • ชาย, 16
        </div>
  
        <div>ประวัติส่วนตัว : ที่อยู่ 288 หมู่ 2 ต.โสกปลาดุก อ.หนองบัวระเหว จ.ชัยภูมิ กำลังศึกษาอยู่วิทยาลัยเทคนิคชัยภูมิ ชั้นปวส.1</div>
        <div>งานอดิเรก/สิ่งที่ชอบ : ชอบเล่นเกม อ่านหนังสือ ฟังเพลง เล่นกีฬา </div>
      </v-card-text>
  
      <v-divider class="mx-4"></v-divider>
  
      <v-card-title>ช่องทางการติดต่อ</v-card-title>
  
     
  
      <v-card-actions>
        <v-btn
          color="deep-purple lighten-2"
          text
          @click="reserve"
        >
          Reserve
        </v-btn>
      </v-card-actions>
    </v-card>
  </template>

<script>
export default {
  data: () => ({
    loading: false,
    selection: 1,
  }),

  methods: {
    reserve () {
      this.loading = true

      setTimeout(() => (this.loading = false), 2000)
    },
  },
}
</script>