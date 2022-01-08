<template>
  <div id="newUser">
    <div class="container">
		<div class="col-md-12">	
			<h1 class="text-center margin-bottom-15">New User Form</h1>		
			<form class="form-horizontal templatemo-contact-form-2 templatemo-container" @submit.prevent="addNewUser">
				<div class="row">
					<div class="col-md-6">
						<div class="form-group">				          		          	
              <div class="col-sm-12">
                <div class="templatemo-input-icon-container">
                  <i class="fa fa-user"></i>
                  <input v-model="name" name="name" class="form-control" placeholder="Name">
                </div>		            		            		            
              </div>              
            </div>
            <div class="form-group">
              <div class="col-sm-12">
                <div class="templatemo-input-icon-container">
                  <i class="fa fa-envelope"></i>
                  <input v-model="email" name="email" class="form-control" placeholder="Email">
                </div>
              </div>
            </div>
            <div class="form-group">
              <div class="col-sm-12">
                <div class="templatemo-input-icon-container">
                  <i class="fa fa-phone"></i>
                  <input v-model="phone" name="phone" class="form-control" placeholder="Phone">
                </div>
              </div>
            </div>
					</div>
				</div>	        
      <div class="form-group">
        <div class="col-md-12" id="submitBtn">
          <button class="btn btn-success">Submit</button>     
        </div>
      </div>		    	
    </form>
	</div>
  </div>

  <div id="userList">
        <ul class="w3-ul w3-card-4">
          <li class="w3-bar" v-for="(user, index) in users" key="user.id">
            <span @click="removeUser(index)" class="w3-bar-item w3-button w3-xlarge w3-right">
              &times;
            </span>
            
            <div class="w3-bar-item">
              <span class="w3-large">{{ user.name }}</span><br>
              <span>{{ user.email }} - {{ user.phone }}</span>
            </div>
          </li>
        </ul>
      </div>
		</div>
</template>

<script>
  import { ref, reactive } from 'vue';

  export default {
    name: 'NewUserForm',
    /*
    methods: {
      async getUser() {
        const res = await fetch('https://randomuser.me/api');
        const { results } = await res.json();
        picture
      }
    },
    data() {
      picture
    },
  */
    setup(){
      const name = ref('');
      const email = ref('');
      const phone = ref('');
      var picture = ref('');

      const users = ref([]);

      function addNewUser(){
        
        //const res = await fetch('https://randomuser.me/api');
        //const { results } = await res.json();
        
        //console.log(results[0]);
        
        //results[0].picture.large

        users.value.push({
          id: Date.now(),
          name: name.value,
          email: email.value,
          phone: phone.value
        });

        
        name.value = '';
        email.value = '';
        phone.value = '';
        
      }

      

      function removeUser(index){
        users.value.splice(index,1);
      }
      

      return {
        addNewUser,
        removeUser,
        name,
        email,
        phone,
        users
      };
    }
  }
</script>
<style>

  @import "https://www.w3schools.com/w3css/4/w3.css";
  @import "https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css";
  @import "https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/3.4.1/css/bootstrap-theme.min.css";
  @import "http://fonts.googleapis.com/css?family=Open+Sans:300,400,700";
  @import "../assets/css/style.css";

  #newUser{
    /*border: 1px solid black;*/
    margin-top: 5rem;
    margin-left: 20rem;
    width: 50%;
  }
  #submitBtn{
    margin-top: 2rem;
  }
  #userList{
    margin-top: 4rem;
  }
</style>