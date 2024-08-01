<template>
    <v-data-table :headers="headers" :items="students" :search="search" :sort-by="[{ key: 'username', order: 'asc' }]">
        <template v-slot:top>
            <v-toolbar flat>

                <v-toolbar-title>My CRUD</v-toolbar-title>
                <v-divider class="mx-4" inset vertical></v-divider>
                <!-- search -->
                <v-text-field v-model="search" label="Search" prepend-inner-icon="mdi-magnify" variant="outlined"
                    hide-details single-line></v-text-field>
                <!-- end search -->
                <v-spacer></v-spacer>
                <v-dialog v-model="dialog" max-width="500px">
                    <template v-slot:activator="{ props }">
                        <v-btn class="mb-2" color="primary" dark v-bind="props">
                            New Item
                        </v-btn>
                    </template>

                    <v-card>
                        <v-card-title>
                            <span class="text-h5">{{ formTitle }}</span>
                        </v-card-title>

                        <v-card-text>
                            <v-container>
                                <v-row>
                                    <v-col cols="12" md="4" sm="6">
                                        <v-text-field v-model="editedItem.id" label="id"></v-text-field>
                                    </v-col>
                                    <v-col cols="12" md="4" sm="6">
                                        <v-text-field v-model="editedItem.username" label="username"></v-text-field>
                                    </v-col>
                                    <v-col cols="12" md="4" sm="6">
                                        <v-text-field v-model="editedItem.password" label="password"></v-text-field>
                                    </v-col>
                                    <v-col cols="12" md="4" sm="6">
                                        <v-text-field v-model="editedItem.email" label="email"></v-text-field>
                                    </v-col>
                                    <v-col cols="12" md="4" sm="6">
                                        <v-text-field v-model="editedItem.picture" label="picture"></v-text-field>
                                    </v-col>
                                    <v-col cols="12" md="4" sm="6">
                                        <v-text-field v-model="editedItem.status" label="status"></v-text-field>
                                    </v-col>
                                </v-row>
                            </v-container>
                        </v-card-text>

                        <v-card-actions>
                            <v-spacer></v-spacer>
                            <v-btn color="blue-darken-1" variant="text" @click="close">
                                Cancel
                            </v-btn>
                            <v-btn color="blue-darken-1" variant="text" @click="save">
                                Save
                            </v-btn>
                        </v-card-actions>
                    </v-card>
                </v-dialog>
                <v-dialog v-model="dialogDelete" max-width="500px">
                    <v-card>
                        <v-card-title class="text-h5">Are you sure you want to delete this item?</v-card-title>
                        <v-card-actions>
                            <v-spacer></v-spacer>
                            <v-btn color="blue-darken-1" variant="text" @click="closeDelete">Cancel</v-btn>
                            <v-btn color="blue-darken-1" variant="text" @click="deleteItemConfirm">OK</v-btn>
                            <v-spacer></v-spacer>
                        </v-card-actions>
                    </v-card>
                </v-dialog>
            </v-toolbar>
        </template>
        <template v-slot:item.actions="{ item }">
            <v-icon class="me-2" size="small" @click="editItem(item)">
                mdi-pencil
            </v-icon>
            <v-icon size="small" @click="deleteItem(item)">
                mdi-delete
            </v-icon>
        </template>
        <template v-slot:no-data>
            <v-btn color="primary" @click="initialize">
                Reset
            </v-btn>
        </template>
    </v-data-table>
</template>
<script>
import axios from 'axios'
import Index from './index.vue';

export default {
    data: () => ({
        search: '',
        dialog: false,
        dialogDelete: false,
        headers: [
            {
                title: 'id',
                align: 'start',
                sortable: false,
                key: 'id',
            },
            { key: 'username', title: 'username' },
            { key: 'password', title: 'password' },
            { key: 'email', title: 'email' },
            { key: 'picture', title: 'picture' },
            { key: 'status', title: 'status' },
            { title: 'Actions', key: 'actions', sortable: false },
        ],
        students: [],
        editedIndex: -1,
        editedItem: {},
        defaultItem: {},
    }),

    computed: {
        formTitle() {
            return this.editedIndex === -1 ? 'เพิ่มข้อมูล' : 'แก้ไขข้อมูล'
        },
    },

    watch: {
        dialog(val) {
            val || this.close()
        },
        dialogDelete(val) {
            val || this.closeDelete()
        },
    },
    
    async created() {
        this.initialize()
        console.log('init list data');
        const response = await axios.get('http://localhost:7000/list')
        this.students = response.data.rows
        
    },

    mounted() {
        let user = window.sessionStorage.getItem('email')
        console.log('users=',user) 
        if (!user) {
            this.$router.replace('/login')
        }else {
            console.log('list')
                window.sessionStorage.setItem("email", response.data.row[0].email)
                this.$router.replace('/list')
        }
      },


    methods: {
        initialize() {
            this.students = [
                {
                    id: 'Frozen Yogurt',
                    username: 159,
                    fat: 6.0,
                    carbs: 24,
                    protein: 4.0,
                },
                {
                    id: 'Ice cream sandwich',
                    username: 237,
                    fat: 9.0,
                    carbs: 37,
                    protein: 4.3,
                },
                {
                    id: 'Eclair',
                    username: 262,
                    fat: 16.0,
                    carbs: 23,
                    protein: 6.0,
                },
                {
                    id: 'Cupcake',
                    username: 305,
                    fat: 3.7,
                    carbs: 67,
                    protein: 4.3,
                },
                {
                    id: 'Gingerbread',
                    username: 356,
                    fat: 16.0,
                    carbs: 49,
                    protein: 3.9,
                },
                {
                    id: 'Jelly bean',
                    username: 375,
                    fat: 0.0,
                    carbs: 94,
                    protein: 0.0,
                },
                {
                    id: 'Lollipop',
                    username: 392,
                    fat: 0.2,
                    carbs: 98,
                    protein: 0,
                },
                {
                    id: 'Honeycomb',
                    username: 408,
                    fat: 3.2,
                    carbs: 87,
                    protein: 6.5,
                },
                {
                    id: 'Donut',
                    username: 452,
                    fat: 25.0,
                    carbs: 51,
                    protein: 4.9,
                },
                {
                    id: 'KitKat',
                    username: 518,
                    fat: 26.0,
                    carbs: 65,
                    protein: 7,
                },
            ]
        },

        editItem(item) {
            this.editedIndex = this.students.indexOf(item)
            this.editedItem = Object.assign({}, item)
            this.dialog = true

        },

        deleteItem(item) {
            this.id = item.id
            console.log(item.id)
            this.dialogDelete = true
        },

        async deleteItemConfirm() {
            console.log('confirm')
            console.log(this.id)
            const response = await axios.get('http://localhost:7000/delete?id=' + this.id)
            this.students = response.data.rows
            this.closeDelete()
        },

        close() {
            this.dialog = false
            this.$nextTick(() => {
                this.editedItem = Object.assign({}, this.defaultItem)
                this.editedIndex = -1
            })
        },

        closeDelete() {
            this.dialogDelete = false
            this.$nextTick(() => {
                this.editedItem = Object.assign({}, this.defaultItem)
                this.editedIndex = -1
            })
        },

        async save() {
            let insert;
            // Insert new item
            if (this.editedIndex === -1) {
                console.log(this.editedItem)
                insert = await axios.post('http://localhost:7000/insert', this.editedItem)
                this.students = insert.data.rows
                this.close()
            } else {
                let update;
                // Update existing item
                console.log(this.editedItem)
                update = await axios.post('http://localhost:7000/update', this.editedItem)
                this.students = update.data.rows
                this.close()
            }


        },
    },
}
</script>