<script>
export default {
  name: ' CardUser',
  data() {
    return {
      message: '',
      color: ''
    }
  },
  props: {
    user: {
      type: Object,
      required: true
    }
  },
  methods: {
    enviarMensaje() {
      this.$emit('enviar-mensaje', this.message, this.color, this.user.name.first, this.user.side)

      this.message = ''
    }
  },
  emits: ['enviar-mensaje']
}
</script>
<template>
  <div class="user-component">
    <h2>CardUser</h2>
    <div class="card">
      <img :src="user.picture.large" class="card-img-top" alt="..." />
      <div class="card-body">
        <h5 class="card-title">{{ user.name.first }} {{ user.name.last }}</h5>

        <!-- Envio de Mensaje -->
        <form @submit.prevent="enviarMensaje">
          <input type="color" v-model="color" class="form-control form-control-color" />
          <textarea v-model="message" class="form-control"></textarea>
          <button class="btn btn-primary mt-2">Enviar</button>
        </form>
      </div>
    </div>
  </div>
</template>
