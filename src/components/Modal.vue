<template>
  <div class="modal__overlay" @click="$emit('close-modal')">
    <div class="modal__wrapper">
      <strong class="modal__title">It's ok</strong>
      <div class="modal__result">
        <span class="modal__license">Chosen license: {{ license }}</span>
        <span class="modal__quantity">Quantity: {{ quantity }}</span>
      </div>
      <button class="modal__close" @click.prevent="$emit('close-modal')">Super!</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    quantity: {
      type: Number,
      required: true
    },
    license: {
      type: Number,
      required: true
    },
  }
}
</script>

<style scoped>

</style>
