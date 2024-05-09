<template>
    <v-card class="mt-5 mx-5">
        <v-card-title>
            <div style="font-weight: 700; color: rgba(1, 5, 131, 0.97)"><h3>DASHBOARD</h3></div>
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
        <v-data-table :headers="studentHeaders" :items="studentInfo" :search="search">
            <template slot="item.action" slot-scope="{ item }">
                <v-btn class="primary">EDIT</v-btn>
                <v-btn class="error">DELETE</v-btn>
            </template>        
        </v-data-table>
    </v-card>
</template>

<script>
export default {
    data() {
        return {
            search: '',
            studentHeaders: [
                { text:'STUDENT ID', align: 'start', filterable: true, value:'studentID'},
                { text:'LASTNAME', value:'lastName'},
                { text:'FIRSTNAME', value:'firstName'},
                { text:'MIDDLENAME', value:'middleName'},
                { text:'COURSE', value:'course'},
                { text:'SECTION', value:'section'},
                { text:'', value:'action'},
            ],
            studentInfo: [
                {
                    studentID: '19-00316',
                    lastName: 'Pinlac',
                    firstName: 'Roengent',
                    middleName: 'Obenario',
                    course: 'IT',
                    section: '3A',
                },
                {
                    studentID: '21-00629',
                    lastName: 'Delos Santos',
                    firstName: 'Charliemane',
                    middleName: 'Nacua',
                    course: 'IT',
                    section: '3A',
                }
            ]
        }
    },
}
</script>