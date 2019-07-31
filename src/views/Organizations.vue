<template>
  <div class="organizations">
   <table>
     <tbody>
       <tr v-for="user in users" :key="user.index">
         <td>{{ user.email }}</td>
       </tr>
     </tbody>
   </table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      users: null
    }
  },
  mounted() {
    this.getUsers()    
  },
  methods: {
    getUsers() {
      axios
        .get('https://randomuser.me/api/?results=10')
        .then( response => {
          this.users = response.data.results
        })
        .catch( e => console.log(e))
    } 
  },
}
</script>
