<template>
  <section class="license">
    <form class="license__form" @submit.prevent="modal = true">

            <modal
                v-show="modal"
                @close-modal="modal = false"
                :quantity="quantity"
                :license="active">
            </modal>

      <license-item
          v-for="(license, key) in licenseItems"
          @active="setActive"
          :active="active"
          :license="license">
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

        <button class="form__submit" type="submit" :disabled="active === 0">Buy now</button>

        <div class="form__selected">
          Selected plan: {{ active }}
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
      const license = this.licenseItems.find(l => l.id === this.active)
      if (license) {
        return license.price * this.quantity;
      }
      return 0;
    }
  }
}
</script>

<style scoped></style>
