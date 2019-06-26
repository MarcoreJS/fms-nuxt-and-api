<template>
    <v-container grid-list-xl fluid>
        <v-layout row wrap>
            <v-flex xs12 sm12 md6>
                <v-text-field v-model="name" label="Nombre"></v-text-field>
            </v-flex>
            <v-flex xs12 sm12 md6>
                <v-text-field v-model="school" label="Escuela"></v-text-field>
            </v-flex>

            <v-flex offset-md9 md3>
                <v-btn @click="saveData()" outline>Guardar</v-btn>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
export default {
    data() {
        return {
            name: "",
            school: ""
        }
    },
    methods: {
        saveData() {
            var config = {
                headers: {
                    "Access-Control-Allow-Origin": "*",
                    "Content-Type": "application/json"
                }
            };
            var new_friend = {
                name: this.name,
                school: this.school
            }
            this.$axios.post("http://127.0.0.1/friends", new_friend,config.headers).then(res => {
                alert("registro exitoso")
            }).catch(e => alert(e.message))
        }
    }
}
</script>



