<template>

  <div class="form__radio-wrapper">

    <input :id="'radio-'+license.id"
           type="radio"
           name="radio"
           :value="license.id"
           :checked="license.id===1"
           @click="$emit('input',license.id)">

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
  },
}
</script>

<style scoped></style>
