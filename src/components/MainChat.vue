<script>
export default {
  name: 'MainChat',
  props: {
    messages: {
      type: Array,
      required: true
    }
  }
}
</script>
<template>
  <h2>Mensajes</h2>

  <div class="main-chat">
    <div
      v-for="(message, index) in messages"
      :key="index"
      class="message"
      :class="message.side == 'left' ? 'text-start' : 'text-end'"
    >
      <span :style="{ backgroundColor: message.color, color: 'white' }">{{ message.name }}</span>
      <p class="mensaje">
        {{ message.message }}
      </p>
    </div>
    <hr />
  </div>
</template>

<style scoped>
.main-chat {
  background-color: #efe6dd;
}
</style>
