<template>
    <v-card class="mt-5 mx-5">
        <v-card-title>
            <div style="font-weight: 700; color: rgba(1, 5, 131, 0.97)"><h3>STUDENT LIST</h3></div>
            <v-spacer />
            <v-col md="4">
                <v-text-field
                    v-model="search"
                    append-icon="mdi-magnify" 
                    label="Search"
                    single-line
                    hide-details   
                    >
                </v-text-field>
            </v-col>
        </v-card-title>
        <v-data-table :headers="studentList" :items="studentInfo" :search="search">
            
        </v-data-table>
    </v-card>
</template>

<script>
export default {
    data() {
        return {
            search: '',
            studentList: [
                { text:'STUDENT #', align: 'start', filterable: true, value:'studentNo'},
                { text:'LASTNAME', value:'lastName'},
                { text:'FIRSTNAME', value:'firstName'},
                { text:'MIDDLENAME', value:'middleName'},
                { text:'COURSE', value:'course'},
                { text:'SECTION', value:'section'},
                { text:'', value:'action'},
            ],
            studentInfo: [
                {
                    studentNo: '',
                    lastName: '',
                    firstName: '',
                    middleName: '',
                    course: '',
                    section: '',
                }
            ]
        }
    },
}
</script>