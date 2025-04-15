<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const email = ref('')
const password = ref('')
const errorMessage = ref('')
const router = useRouter() // ¡Importantísimo!

const handleLogin = async () => {
  console.log('¡Formulario enviado!') // Para verificar que la función se ejecuta
  try {
    const response = await fetch(
      'https://palevioletred-mole-765673.hostingersite.com/api/public/api/wp/login',
      {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          username: email.value,
          password: password.value,
        }),
      },
    )

    const data = await response.json()
    console.log('Respuesta de la API:', data) // Para ver la respuesta de la API
    console.log('data.success:', data.success, typeof data.success) // Para verificar el tipo y valor de data.success

    if (data.success === true) {
      // ¡Asegúrate de que la condición sea correcta!
      console.log('Redirigiendo a /dashboard') // Para verificar la redirección
      localStorage.setItem('authToken', data.token)
      if (data.user) {
        localStorage.setItem('userData', JSON.stringify(data.user))
      }
      router.push('/dashboard')
    } else {
      errorMessage.value = data.message || 'Error de autenticación.'
      alert(errorMessage.value)
    }
  } catch (error) {
    console.error('Error al iniciar sesión:', error)
    alert('Error de conexión con el servidor. Inténtalo de nuevo.')
  }
}
</script>

<template>
  <div class="login-container">
    <div class="login-box">
      <div class="logo">Loto</div>
      <h2>Iniciar sesión en<br />Suscripciones</h2>

      <form @submit.prevent="handleLogin">
        <label>Email</label>
        <input
          type="email"
          id="username"
          v-model="email"
          placeholder="nombre@ejemplo.com"
          required
        />

        <label class="password-label">
          Contraseña
          <a href="#" class="forgot">¿Olvidaste tu contraseña?</a>
        </label>
        <input type="password" id="password" v-model="password" required />

        <button type="submit" class="btn btn-primary w-100">Iniciar sesión</button>
      </form>

      <div class="separator">
        <span>o</span>
      </div>

      <div class="register">¿No tienes una cuenta? <a href="#">Regístrate</a></div>
    </div>
  </div>
</template>

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
