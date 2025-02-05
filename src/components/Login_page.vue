<template>

    <div class='container'>
        <div class='container1'>
            <h1>Login</h1>
            <div class='input_box'>
    
                <input type='email' v-model="input_email" name='email' id='email' autoComplete='off' autofocus placeholder='Enter your Email'  />
                <i class="fa-solid fa-user"></i><i class="fa-regular fa-user"></i>
                <p>{{ message_error }}</p>
               
            </div>
    
            <div class='input_box'>
    
                <input :type="show_password ? 'text' : 'password'" name='password' v-model="input_password" id='password' placeholder='Password' autoComplete='off' />
                <i class='bx bxs-lock-alt'></i><i @click="togglepassword()" class="fa-regular fa-user"></i>
                
            </div>
            <div class='remember_forgot'>   
                <label for="checkbox"><input type='checkbox' v-model="remember_me"  value="remembered" id="checkbox" />Remember me</label>
                <!-- in below input field we take "name" attribute same for check only one value -->
                <!-- <input type='radio' value="student" name="who" v-model="form.who" id="student" /><label for="student">student</label>
                <input type='radio' value="devloper" name="who" v-model="form.who" id="devloper" /><label for="devloper">devloper</label> -->
                <a href="forgot">Forgot Password?</a>
            </div>
            <button type='submit' v-on:click="handleLogin" :disabled="loading"> {{loading ? "logging..." :"Login"}}</button>
            <div class='register_link'>
                <p>Don't have an account?<a href='/signin'>Register</a></p>
            </div>
        </div>
    </div>
    </template>
    <script>
   import { ref } from "vue"; 

export default {
  setup() {
    const input_email = ref("");
    const input_password = ref("");
    const remember_me = ref(false);
    const message_error = ref("");
    const loading = ref(false);
    const show_password = ref(false);

    const togglepassword=()=>{
        show_password.value = !show_password.value;
    };

    const handleEmailPattern=(email)=>{
        
    }
    const handleLogin = () => {
        if(!input_email.value){
            message_error.value = "email is required"
            return;
        }
        loading.value=true;
        message_error.value=""
       setTimeout(()=>{
      console.log("Email:", input_email.value);
      console.log("Password:", input_password.value);
      console.log("Remember Me:", remember_me.value);
      loading.value=false;},2000);
    };

    return {
      input_email,
      input_password,
      remember_me,
      handleLogin,
      message_error,
      loading,
      show_password,
      togglepassword
    };
  },
};
</script>
     <style scoped>
     * {
         margin: 0;
         padding: 0;
         box-sizing: border-box;
         font-family: "poppins", sans-serif;
     }
     
     .container {
         display: flex;
         justify-content: center;
         align-items: center;
         height: 100vh;
       
         background-color: #333;
         
     }
     
     .container1 {
         width: 420px;
         background: transparent;
         border: 2px solid rgba(255, 255, 255, .2);  
         backdrop-filter: blur(10px);
         box-shadow: 0 0 10px rgba(0, 0, 0, .2);
         color: aliceblue;
         border-radius: 10px;
         padding: 10px 20px;
     }
     
     h1 {
         font-size: 36px;
         text-align: center;
     }
     
     .container1 .input_box {
         position: relative;
         width: 100%;
         height: 50px;
         margin: 30px 0;
     }
     
     .input_box input {
         width: 100%;
         height: 100%;
         background: transparent;
         border: none;
         outline: none;
         border: 2px solid rgba(255, 255, 255, .2);
         border-radius: 40px;
         font-size: 16px;
         color: aliceblue;
         padding: 20px 45px 20px 20px;
     }
     
     .input_box input::placeholder {
         color: #dbcfcf;
     
     }
     
     .input_box i {
         position: absolute;
         right: 20px;
         top: 50%;
         transform: translateY(-50%);
         font-size: 20px;
     
     }
     
     .container1 .remember_forgot {
         display: flex;
         justify-content: space-between;
         font-size: 14.5px;
         margin: -15px 0 15px;
     }
     
     .remember_forgot label input {
         accent-color: #fff;
         margin-right: 3px;
     }
     
     .remember_forgot a {
         color: #fff;
         text-decoration: none;
     }
     
     .remember_forgot a:hover {
         text-decoration: underline;
     
     }
     
     .container1 button {
         width: 100%;
         height: 45px;
         background: #fff;
         border: none;
         outline: none;
         border-radius: 40px;
         box-shadow: 0 0 10px rgba(0, 0, 0, .1);
         cursor: pointer;
         font-size: 16px;
         color: #333;
         font-weight: 600;
     }
     
     .container1 .register_link {
         font-size: 14.5px;
         text-align: center;
         margin: 20px 0 15px;
     }
     
     .register_link p a {
         color: #fff;
         text-decoration: none;
         font-weight: 600;
     }
     
     .register_link p a:hover {
         text-decoration: underline;
     
     }
     i{
        color: #dbcfcf;
     }
     </style>