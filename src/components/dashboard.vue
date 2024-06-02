<template>
  <div class="dashboard-container">
    <Navbar />
    <h1>Hello Dashboard</h1>
    <h2>Contact List</h2>
    <table class="table table-hover">
      <thead>
        <tr>
          <th  scope="col">ID:</th>
          <th  scope="col">Name:</th>
          <th  scope="col">Email:</th>
          <th  scope="col">Designation:</th>
          <th  scope="col">Contact No.</th>
          <th  scope="col">Action</th>
        </tr>
      </thead>
      
      <tbody v-for="contact in contacts" :key="contact.id">
        <tr class="table-secondary">
          <th scope="row">{{ contact.id }}</th>
          <th scope="row">{{ contact.name }}</th>
          <th scope="row">{{ contact.email }}</th>
          <th scope="row">{{ contact.designation }}</th>
          <th scope="row">{{ contact.Contact_no }}</th>
          <th scope="row"><router-link :to="{ name: 'EditContact', params: { id: contact.id } }">Edit</router-link></th>
          <th scope="row"><button @click.prevent="deleteContact(contact.id)">Delete</button></th>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import Navbar from './Navbar.vue';
import axios from 'axios';
export default {
  name: 'Contactlist',
  data(){
    return{
      contacts:Array
    }
  },
  created(){
    this.getContacts();
  },
  components: {
    Navbar
  },
  methods: {
    async getContacts() {
      let url = 'http://127.0.0.1:8000/api/contacts';
      await axios.get(url).then(response => {
        this.contacts = response.data.contacts;
        console.log(this.contacts);
      }).catch(error => {
        console.log(error);
      })
    },
   async deleteContact(id) {
      let url = `http://127.0.0.1:8000/api/delete_contact/${id}`;
      await axios.delete(url).then(response =>{
        if(response.status == 200) {
          alert(response.data.message);
          this.getContacts();
        }
      }).catch(error =>{
        console.log(error);
      });
    },
    logout() {
      this.$router.push('/'); // Redirect to the login page after logout
    }
  },
  mounted() {
    console.log('Ni connect siya yey.');
  }
};
</script>

<style scoped>
/* Add your dashboard styles here */
</style>
