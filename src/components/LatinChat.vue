<script>
import axios from 'axios'
import CardUser from './CardUser.vue'
import MainChat from './MainChat.vue'
export default {
  name: 'LatinChat',
  components: {
    CardUser,
    MainChat
  },
  data() {
    return {
      userDerecha: {},
      userIzquierda: {},
      messages: []
    }
  },
  async created() {
    try {
      const url = 'https://randomuser.me/api/?results=2'
      const { data } = await axios.get(url)

      this.userDerecha = { ...data.results[0], side: 'right' }
      this.userIzquierda = { ...data.results[1], side: 'left' }
    } catch (error) {
      console.log(error)
    }
  },
  methods: {
    enviarMensaje(message, color, name, side) {
      this.messages.push({ message, color, name, side })
    }
  }
}
</script>
<template>
  <h1>Güelcom</h1>
  <div class="chat-app-container container">
    <div class="row">
      <div class="col-4">
        <CardUser
          :user="userIzquierda"
          @enviar-mensaje="enviarMensaje"
          v-if="Object.keys(userIzquierda).length > 0"
        />
      </div>
      <div class="col-4">
        <MainChat :messages="messages" />
      </div>
      <div class="col-4">
        <CardUser
          :user="userDerecha"
          @enviar-mensaje="enviarMensaje"
          v-if="Object.keys(userDerecha).length > 0"
        />
      </div>
    </div>
  </div>
</template>
<style scoped></style>
