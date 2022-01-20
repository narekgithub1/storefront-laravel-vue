<template>
  <div class="container register-form">
    <div class="form">

      <form action="" @submit ="postData" method="post">
      <div class="form-content">
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <input type="text" class="form-control" placeholder="Your Name *"  v-model="form.name" />
            </div>
            <div class="form-group">
              <input type="text" class="form-control" placeholder="Your Email *" v-model="form.email"/>
            </div>
          </div>
          <div class="col-md-6">
            <div class="form-group">
              <input type="password" class="form-control" v-model="form.password" placeholder="Your Password *" />
            </div>

            <div class="form-group">
              <label for=""> Choose your Role</label>
              <select name="Role" id="" v-model="form.role">
                <option value="1">Seller</option>
                <option value="2">Buyer</option>
              </select>
            </div>
          </div>
        </div>
        <button type="submit" class="btnSubmit">Submit</button>
      </div>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios"

export default {
  name: 'Register',
  data () {
    return {
      form: {
        "name": '',
        "password":'',
        "email": '',
        "role_id": null
      },
    }
  },
  methods : {
  postData() {
      axios.post('http://store.loc/api/user/register', this.form)
          .then((res) => {
            console.log(res);
          });
    }
 }
}

</script>



<style scoped>
* {box-sizing: border-box}

/* Add padding to containers */
.container {
  padding: 16px;
}

/* Full-width input fields */
input[type=text], input[type=password] {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #f1f1f1;
}

input[type=text]:focus, input[type=password]:focus {
  background-color: #ddd;
  outline: none;
}

/* Overwrite default styles of hr */
hr {
  border: 1px solid #f1f1f1;
  margin-bottom: 25px;
}

/* Set a style for the submit/register button */
.registerbtn {
  background-color: #04AA6D;
  color: white;
  padding: 16px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
  opacity: 0.9;
}

.registerbtn:hover {
  opacity:1;
}

/* Add a blue text color to links */
a {
  color: dodgerblue;
}

/* Set a grey background color and center the text of the "sign in" section */
.signin {
  background-color: #f1f1f1;
  text-align: center;
}
</style>