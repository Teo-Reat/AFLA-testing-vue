<template>
  <section class="license">
    <form class="license__form" @submit.prevent="modal = true">

      <modal
          v-show="modal"
          @close-modal="modal = false"
          :quantity="quantity"
          :license="licenseItems[active].id">
      </modal>

      <license-item
          v-for="(license, key) in licenseItems"
          @active="setActive"
          :class="{ active: active === key }"
          :licenkey="key"
          :license="license">
        {{ license }} {{ key }}
      </license-item>

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

        <div class="form__total">TOTAL: <span class="form__total-sum">$ {{ price }}</span></div>

        <button class="form__submit" type="submit">Buy now</button>

        <div class="form__selected">
          Selected plan: {{ licenseItems[active].id }}
        </div>
      </div>

    </form>
  </section>
</template>

<script>
import LicenseItem from "@/components/LicenseItem";
import Modal from "@/components/Modal";

export default {
  components: {
    LicenseItem,
    Modal
  },
  data() {
    return {
      licenseItems: [
        {id: 1, price: 13},
        {id: 5, price: 22},
        {id: 42, price: 34}
      ],
      active: 0,
      quantity: 1,
      modal: false
    }
  },

  methods: {
    setActive(payload) {
      this.active = payload
    },
  },

  computed: {
    price() {
      return this.licenseItems[this.active].price * this.quantity
    }
  }
}
</script>

<style scoped></style>
