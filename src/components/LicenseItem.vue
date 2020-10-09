<template>

  <div class="form__radio-wrapper" :class="{ active: license.id === active}">

    <input
        type="radio"
        @click="$emit('active', license.id)"
        :value="license.id"
        :checked="license.id === active"
        :id="'radio-'+license.id">

    <label :for="'radio-'+license.id">

          <span class="form__radio-description">
            Licence plan # {{ license.id }}
          </span>

          <span class="form__price">
              ${{ license.price }} per license
          </span>

    </label>

  </div>

</template>

<script>
export default {
  name: "LicenseItem",
  props: {
    license: {
      type: Object,
      required: true
    },
    active: {
      type: Number,
      required: true
    },
  },
  data() {
    return {
      // active: 0
    }
  },

  methods: {

  }
}
</script>

<style scoped></style>
