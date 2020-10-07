<template>
  <section class="license">
    <form action="" class="license__form form">

      <license-item :license="license"
                    v-model="active"
                    v-for="license in licenseItems"
                    :key="license.id"/>
      <div class="form__select-wrapper">

        <label for="quantity">
          <span class="form__select-description">
            Number of licenses:
          </span>
        </label>

        <select name="quantity" id="quantity" class="form__select" v-model="quantity">
          <option :value="option" class="form__option" v-for="option in 10">{{ option }}</option>
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
  data() {
    return {
      licenseItems: [
        {id: 1, price: 13},
        {id: 2, price: 22},
        {id: 3, price: 34}
      ],
      active: 1,
      quantity: 1
    }
  },
  computed: {
    getSum() {
      return this.price * this.quantity
    },
    price() {
      const license = this.licenseItems.find(license=>license.id === this.active)
      if(license){
        return license.price;
      }
      return 0;
    }
  }
}
</script>

<style scoped></style>
