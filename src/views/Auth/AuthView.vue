<template>
    <div class="login-container">
      <div class="login-box">
        <div class="logo">Loto</div>
        <h2>Iniciar sesión en<br />Suscripciones</h2>
  
        <form @submit.prevent="handleLogin">
          <label>Email</label>
          <input type="email" v-model="email" placeholder="nombre@ejemplo.com" required />
  
          <label class="password-label">
            Contraseña
            <a href="#" class="forgot">¿Olvidaste tu contraseña?</a>
          </label>
          <input type="password" v-model="password" required />
  
          <button type="submit" class="btn btn-primary w-100">Iniciar sesión</button>
        </form>
  
        <div class="separator">
          <span>o</span>
        </div>
  
        <div class="register">
          ¿No tienes una cuenta? <a href="#">Regístrate</a>
        </div>
      </div>
    </div>
  </template>
  
  
  
  <script>
  export default {
    data() {
      return {
        email: '',
        password: ''
      };
    },
    methods: {
      handleLogin() {
        console.log('Iniciar sesión con:', this.email, this.password);
      }
    }
  };
  </script>
  
  <style scoped>
  
  .login-container {
    background-color: #000;
    color: white;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100vw;
  }
  
  .login-box {
    /* width: ; */
    max-width: 400px;
    padding: 2rem;
    background-color: #000;
    text-align: center;
  }
  
  .logo {
    font-size: 2rem;
    margin-bottom: 1rem;
  }
  
  h2 {
    font-size: 1.5rem;
    margin-bottom: 2rem;
  }
  
  label {
    display: block;
    text-align: left;
    margin-bottom: 0.3rem;
    font-weight: bold;
  }
  
  .password-label {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .forgot {
    font-size: 0.85rem;
    color: #1da1f2;
    text-decoration: none;
  }
  
  input {
    width: 100%;
    padding: 0.5rem;
    margin-bottom: 1rem;
    background-color: #111;
    border: 1px solid #333;
    color: white;
    border-radius: 4px;
  }
  
  .separator {
    display: flex;
    align-items: center;
    margin: 1rem 0;
    color: #888;
  }
  
  .separator span {
    flex: 1;
    text-align: center;
    position: relative;
  }
  
  .separator span::before,
  .separator span::after {
    content: '';
    height: 1px;
    background-color: #333;
    position: absolute;
    top: 50%;
    width: 45%;
  }
  
  .separator span::before {
    left: 0;
  }
  
  .separator span::after {
    right: 0;
  }
  
  .register {
    margin-top: 1rem;
    font-size: 0.9rem;
  }
  
  .register a {
    color: #1da1f2;
    text-decoration: none;
  }
  </style>