<template>
  <div id="login-form">
    <div class="container">
      <label for="name">
        <b> UserName</b>
      </label>
      <input type="text" v-model="name" placeholder="Enter Username" name="name" required>

      <label for="email">
        <b>Email: </b> 
      </label>
      <input type="text" v-model="email" placeholder="Enter Email or PhoneNumber" name="email" required>

      <label for="password">
        <b>Password:</b>
      </label>
      <input type="password" v-model="password" placeholder="Enter Password" required>

      <button class="sign-in" type="submit" @click="login">Sign in Page</button>
    </div>

    <div class="container" style="background-color:#f1f1f1">
      <button type="button" class="cancelbtn">Cancel</button>
      <span class="password">Forgot
        <a href="#">password?</a>
      </span>
    </div>

    <h3> Create new Account</h3>
  </div>

</template>
<script>
import firebase from "firebase/compat/app";
import "firebase/compat/auth";

export default {

  data() {
    return {
      name: null,
      email: '',
      password: ''
    }
  },

  methods: {

    login() {
      try {
        firebase 
          .auth()
          .createUserWithEmailAndPassword(this.email, this.password)
        alert('Successfully registered! Please login.');
        this.$router.push('/feed');
      }
      catch (error) {
        alert(error.message);
      } finally {
        this.name = '';
        this.email = '';
        this.password = '';
      }

    }
  }
}

</script>

<style scoped>
/* Bordered form */
#login-form {
  width: 700px;
  align-items: center;
  justify-content: center;
  margin: auto;
}

form {
  border: 3px solid #f1f1f1;
}

/* Full-width inputs */
input[type=text],
input[type=password] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}

/* Set a style for all buttons */
button {
  background-color: #04AA6D;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
}

/* Add a hover effect for buttons */
button:hover {
  opacity: 0.8;
}

.sign-in {
  font-size: 1rem;
}

/* Extra style for the cancel button (red) */
.cancelbtn {
  margin-left: 15px;
  width: auto;
  padding: 10px 18px;
  background-color: #f4367f;
  border-radius: 10px;
}

/* Center the avatar image inside this container */
.imgcontainer {
  text-align: center;
  margin: 24px 0 12px 0;
}


/* Add padding to containers */
.container {
  /* padding-right:25px; */
  margin-top: 5px;
}

/* The "Forgot password" text */
span.password {
  float: right;
  padding: 16px 5px;
  margin-right: 15px;
}

h3 {
  cursor: pointer;
  text-align: center;
  justify-content: center;
  font-size: 1.7rem;
  font-weight: bold;
  color: blue;
  padding: 15px;
  background: #E4E0E0;
}

/* Change styles for span and cancel button on extra small screens */
@media screen and (max-width: 300px) {
  span.password {
    display: block;
    float: none;
  }

  .cancelbtn {
    /* padding-left: 15px !important; */
    width: 100%;
  }
}
</style>