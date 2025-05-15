<template>
<button @click="getUser()">getUser</button>
  <div class="container">
    <img :src="picture" />
        <h2>{{firstname }}</h2>
        <h2>{{ secondname }}</h2>
        <p> {{ email }}</p>    
  </div>

</template>
<script>
export default{
        name: "Contact-component",
        
        data () {
return {
 firstname: "Victor",
secondname: "Cooper",
        
email: "Victor.cooper@exmaple.com",
picture: 
"https://randomuser.me/api/portraits/thumb/men/73.jpg",
            
        };
},
   methods: {
        async getUser() {
          try {
            const response = await fetch('https://randomuser.me/api/')
            const data = await response.json()
            
          
            this.firstname = data.results[0].name.first
            this.secondname = data.results[0].name.last 
                this.email = data.results[0].email
                this.picture = data.results[0].picture.large
          } catch (error) {
            console.error('Error fetching user:', error)
          }
        },
     
        }
      }     
</script>