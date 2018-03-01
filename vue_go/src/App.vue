<template>
    <div id="app" class="container">
            
            
            <br>
        <div v-if="users && users.length" class="row">
            
            <div class="col-4" v-for="user of users">
                      <div  class="card testimonial-card" >

        <!--Bacground color-->
        <div class="card-up indigo lighten-1">
        </div>

        <!--Avatar-->
        <div class="avatar mx-auto white"><img src="https://mdbootstrap.com/img/Photos/Avatars/img%20%2810%29.jpg" class="rounded-circle">
        </div>

        <div class="card-body">
            <!--Name-->
            <h4 class="card-title">{{user.Name}}</h4>
            <hr>
            <!--Quotation-->
            <p><i class="fa fa-quote-left"></i> {{user.Email}}</p>
        </div>

    </div>
    <!--/.Card-->

            </div>
                <!--Card-->

        </div>
                                

        <ul v-if="errors && errors.length">
            <li v-for="error of errors">
                {{error.message}}
            </li>
        </ul>
    </div>

</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      users: [],
      errors: []
    };
  },

  // Fetches posts when the component is created.
  created() {
    axios
      .get(`http://localhost:10000/users`)
      .then(response => {
        // JSON responses are automatically parsed.
        this.users = response.data;
        console.log(this.users);
      })
      .catch(e => {
        this.errors.push(e);
      });
  }
};
</script>