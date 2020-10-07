<template>

  <div class="form__radio-wrapper">

    <input :id="'radio-'+license"
           type="radio"
           name="radio"
           :value="license"
           :checked="license===1"
           @click="$emit('set-radio')">

    <label :for="'radio-'+license">

          <span class="form__radio-description">
            Licence plan # {{ license }}
          </span>

          <span class="form__price">
              ${{ price }} per license
          </span>

    </label>

  </div>

</template>

<script>
export default {
  name: "LicenseItem",
  props: {
    license: {
      type: Number,
      required: true
    },
    price: {
      type: Number,
      required: true
    }
  },

  data() {
    return {
      isActive: 'hello'
    }
  },
}
</script>

<style scoped>
.form__radio-wrapper {
  border: 1px solid transparent;
}

.form__radio-wrapper input[type=radio] {
  display: none;
}

.form__radio-wrapper label {
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
  position: relative;
  padding-left: 55px;
  margin-right: 0;
  line-height: 18px;
  user-select: none;
}

.form__radio-wrapper label::before,
.form__radio-wrapper label::after {
  content: "";
  display: inline-block;
  width: 18px;
  height: 18px;
  position: absolute;
  left: 15px;
  bottom: 11px;
  background: transparent;
  border-radius: 50%;
  border: 4px solid #DBDBDB;
}

.form__radio-wrapper label::after {
  background: #0294BF;
  height: 10px;
  width: 10px;
  border: none;
  display: none;
  left: 23px;
  bottom: 19px;
}

.form__radio-description {
  color: #787878;
  font-size: 18px;
  padding: 14px 0;
  display: inline-block;
}

.form__price {
  color: #969696;
  font-size: 12px;
  display: inline-block;
  margin-right: 15px;
}

/* Checked */
.form__radio-wrapper input[type=radio]:checked + label::before {
  background: transparent;
  border-color: #34648E;
}

.form__radio-wrapper input[type=radio]:checked + label::after {
  display: block;
}

.active {
  background: #EBF4F7;
  border: 1px solid #BCD9E3;
}
</style>
