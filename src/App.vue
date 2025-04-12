
<template>
  <div class="login-container">
    <div class="login-box">
      <div class="logo"> <h1>Loto</h1>
        <!-- <img src="https://cdn-icons-png.flaticon.com/512/124/124021.png" alt="Logo" width="32" /> -->
      </div>
      <h2>Crear tu cuenta</h2>

      <form @submit.prevent="handleRegister">
        <label>Nombre completo</label>
        <input type="text" v-model="fullName" placeholder="Tu nombre" required />

        <label>Email</label>
        <input type="email" v-model="email" placeholder="nombre@ejemplo.com" required />

        <label>Contraseña</label>
        <input type="password" v-model="password" required />

        <label>Confirmar contraseña</label>
        <input type="password" v-model="confirmPassword" required />

        <div class="terms">
          <input type="checkbox" v-model="accepted" id="terms" />
          <label for="terms">
            Acepto los <a href="#">términos y condiciones</a> y la <a href="#">política de privacidad</a>
          </label>
        </div>

        <button type="submit" class="btn-primary">Crear cuenta</button>
      </form>

      <div class="register">
        ¿Ya tienes una cuenta? <a href="#">Iniciar sesión</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      fullName: '',
      email: '',
      password: '',
      confirmPassword: '',
      accepted: false
    };
  },
  methods: {
    handleRegister() {
      if (this.password !== this.confirmPassword) {
        alert('Las contraseñas no coinciden.');
        return;
      }
      if (!this.accepted) {
        alert('Debes aceptar los términos y condiciones.');
        return;
      }
      console.log('Registrando:', this.fullName, this.email);
    }
  }
};
</script>

<style scoped>
.login-container {
  background-color: #000;
  color: white;
  height: 100vh;
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
}

.login-box {
  max-width: 100vw;
  padding: 2rem;
  background-color: #000;
  text-align: center;
}

.logo {
  
}

h2 {
  font-size: 1.1rem;
  margin-bottom: 2rem;
}

label {
  display: block;
  text-align: left;
  margin-bottom: 0.3rem;
  font-weight: bold;
  color: #ddd;
}

input[type="text"],
input[type="email"],
input[type="password"] {
  width: 100%;
  padding: 0.30rem;
  margin-bottom: 1rem;
  background-color: #1a1a1a;
  border: 1px solid #2c2c2c;
  color: #e0e0e0;
  border-radius: 6px;
  font-size: 1rem;
}

.btn-primary {
  width: 100%;
  background-color: #1da1f2;
  color: white;
  border: none;
  padding: 0.30rem;
  font-size: 1rem;
  border-radius: 6px;
  cursor: pointer;
  margin-top: 0.5rem;
}

.social-btn:hover {
  background-color: #222;
}

.terms {
  display: flex;
  align-items: start;
  gap: 0.5rem;
  margin: 1rem 0;
  font-size: 0.85rem;
  text-align: left;
}

.terms input[type="checkbox"] {
  margin-top: 0.2rem;
}

.terms a {
  color: #1da1f2;
  text-decoration: none;
}

.register {
  margin-top: 1rem;
  font-size: 0.9rem;
  color: #bbb;
}

.register a {
  color: #1da1f2;
  text-decoration: none;
}
</style>