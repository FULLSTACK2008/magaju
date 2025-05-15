<template>
  <div class="container">
    <button @click="getUser">Get User</button>

    <div 
    class="card" v-for="(user, index) in users" :key="index">
      <img :src="user.picture.large" />
      <h2>First name:{{ user.login.username }}</h2>
      <p>Email: {{ user.email }}</p>
      <p>Date of Birth: {{ formatDate(user.dob.date) }}</p>
      <p>Location: {{ user.location.city }}, {{ user.location.country }}</p>
      <p>Phone:{{ user.phone }}</p>
    </div>

    
  </div>
</template>

<script>
export default {
 name:"About-component",
  data() {
    return {
      
    }
  },
  methods: {
    async getUser() {
      try {
        const response = await fetch('https://randomuser.me/api/')
        const data = await response.json()
        this.users = [data.results[0]]
      } catch (error) {
        console.error('Error fetching user:', error)
      }
    },
    formatDate(dateStr) {
      const date = new Date(dateStr)
      return date.toLocaleDateString()
    }
  }
}
</script>

<style>
.container {
  text-align: center;
  margin-top: 30px;
  font-family: Arial, sans-serif;
}

button {
  padding: 10px 20px;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 8px;
  font-weight: bold;
  cursor: pointer;
  margin: 20px;
}

button:hover {
  background-color: #2980b9;
}

.card {
  margin-top: 20px;
  padding: 20px;
  display: inline-block;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  text-align: left;

}

.card img {
  border-radius: 50%;
  width: 100px;
  height: 100px;
}

.card h2 {
  margin: 10px 0;
}

.card p {
  margin: 5px 0;
}
</style>

