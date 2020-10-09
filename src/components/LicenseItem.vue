<template>

  <div class="form__radio-wrapper">

    <input
        type="radio"
        name="radio"
        @click="$emit('active', licenkey)"
        :value="license.id"
        :id="'radio-'+license.id"
        :checked="licenkey === 0">

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
    licenkey: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      active: 0
    }
  },

  methods: {

  }
}
</script>

<style scoped></style>
