<template>
  <section class="license">
    <form action="" class="license__form form">

      <license-item :license="license.id"
                    :price="license.price"
                    :class="{ active: license.id === active }"
                    @set-radio="setRadio(key, license.price)"
                    v-for="(license, key) in licenseItems">
      </license-item>

      <div class="form__select-wrapper">

        <label for="quantity">
          <span class="form__select-description">
            Number of licenses:
          </span>
        </label>

        <select name="quantity" id="quantity" class="form__select" v-model="quantity">
          <option :value="opt" class="form__option" v-for="opt in 10">{{ opt }}</option>
        </select>

      </div>

      <div class="form__total-wrapper">

        <div class="form__total">TOTAL: <span class="form__total-sum">${{ getSum }}</span></div>

        <button class="form__submit" type="submit">Buy now</button>

        <div class="form__selected">
          Selected plan: #{{ active }}
        </div>
      </div>

    </form>
  </section>
</template>

<script>
import LicenseItem from "@/components/LicenseItem";

export default {
  components: {
    LicenseItem
  },
  name: "License",
  data() {
    return {
      licenseItems: [
        {id: 1, price: 13},
        {id: 2, price: 22},
        {id: 3, price: 34}
      ],
      active: 1,
      quantity: 1,
      price: 0
    }
  },
  mounted() {
    this.price = this.licenseItems[0].price
  },

  methods: {
    setRadio(id, price) {
      this.active = ++id
      this.price = price
    },
  },

  computed: {
    getSum: function () {
      return this.price * this.quantity
    }
  }
}
</script>

<style scoped>
.license {
  border: 7px solid #EBEBEB;
  width: 370px;
  box-sizing: border-box;
  margin: 30px auto;
  padding: 20px 10px;
}

.form__select-wrapper {
  text-align: center;
  padding: 25px 0;
  position: relative;
  margin-top: 5px;
}

.form__select-wrapper::before,
.form__select-wrapper::after {
  position: absolute;
  display: block;
  content: '';
  height: 1px;
  width: 100%;
  top: 0;
  background: #CCCCCC;
}

.form__select-wrapper::after {
  top: auto;
  bottom: 0;
  color: #CCCCCC;
}

.form__select-description {
  font-size: 12px;
  margin-right: 10px;
}

.form__total {
  font-size: 22px;
  color: #787878;
  margin-top: 20px;
}

.form__total-wrapper {
  text-align: center;
}

.form__total-sum {
  color: #3388A8;
  position: relative;
}

.form__total-sum::after {
  position: absolute;
  display: block;
  content: 'US';
  width: 10px;
  height: 10px;
  right: -10px;
  top: 2px;
  font-size: 12px;
}

.form__submit {
  background: #33A845;
  padding: 10px 35px;
  border: none;
  border-radius: 17px;
  color: white;
  text-transform: uppercase;
  margin-top: 15px;
}

.form__selected {
  color: #0294BF;
  margin-top: 30px;
}
</style>
