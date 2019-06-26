<template>
  <v-layout row wrap>
    <v-flex sm12>
      <v-data-table :headers="headers" :items="friends">
        <template v-slot:items="props">
          <td>{{ props.item.name }}</td>
          <td>{{ props.item.school }}</td>
        </template>
      </v-data-table>
    </v-flex>
    <v-flex xs12 sm8 md6>
      <v-btn to="/new-friend">Añadir Amigo</v-btn>
    </v-flex>
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  data() {
    return {
      friends: [],
      headers: [
        { text: "Nombre", value: "name" },
        { text: "Escuela", value: "school" }
      ]
    }
  },
  created() {
    var config = {
        headers: {
          "Access-Control-Allow-Origin": "*",
          "Content-Type": "application/json"
        }
      };
    this.$axios.get("http://127.0.0.1/friends").then(res => {
      this.friends = res.data;
      console.log(res.data)
    })
  }
}
</script>
