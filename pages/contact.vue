<template>
  <div class="content">
    <Navigation />
    <div class="contact-form">
      <form>
        <div class="field">
          <label>Naam</label>
          <input v-model="form.name" type="text" placeholder="Voer uw naam in">
        </div>
        <div class="field">
          <label>E-mail</label>
          <input v-model="form.email" type="email" placeholder="Voer uw e-mail in" />
        </div>
        <div class="field">
          <label>Bericht</label>
          <textarea v-model="form.message" cols="30" rows="10" placeholder="Voer uw bericht in"></textarea>
        </div>
        <button class="contact-form__submit" @click="submitForm">Versturen</button>
        <div class="contact-form__response" v-if="form.response.show" :class="{ error: form.response.error }">
          <span>{{ form.response.message }}</span>
        </div>
      </form>
    </div>
    <Footer />
  </div>
</template>
  
<script>
import Footer from '../components/Footer.vue';
import Navigation from '../components/Navigation.vue';

export default {
  head: {
    title: "Contact | Lucas van Borkulo"
  },
  components: { Navigation, Footer },
  data() {
    return {
      form: {
        name: new String(),
        email: new String(),
        message: new String(),
        response: {
          message: new String(),
          error: false,
          show: false,
        }
      }
    }
  },
  methods: {
    /**
     * Validate the form in the front-end.
     * 
     * @return {Boolean}
     */
    validateForm() {
      const { name, email, message } = this.form;
      if (name.length <= 2)
        return false;
      if (email.length <= 5)
        return false;
      if (message.length <= 6)
        return false;

      return true;
    },
    /**
     * Submit the form to the back-end.
     * 
     * @todo Add request logic to this function once back-end has been completed.
     * @return {void}
     */
    submitForm() {
      if (!this.validateForm()) {
        this.sendResponse("Het formulier is niet compleet", true);
        return;
      }
      this.sendResponse("Het formulier is verzonden");
    },
    /**
     * Send a response to the form user.
     * 
     * @return {void}
     */
    sendResponse(message, isError = false) {
      const response = this.form.response;
      response.message = message;
      response.error = isError;
      response.show = true;

      setTimeout(() => response.show = false, 5000);
    }
  }
}
</script>
<style scoped lang="scss">
.content {

  .contact-form {
    display: flex;
    flex-direction: column;
    align-items: center;

    &__submit {
      border-radius: 0px;
      background-color: #f8f8f8;
      padding-block: 8px;
      border-width: 1px;
      border-color: #000000;

      &:hover {
        cursor: pointer;
      }
    }

    &__response {
      background-color: #f8f8f8;
      padding: 6px;
      text-align: center;
    }

    &__response.error {
      background-color: #ff0000;
      color: #ffffff;
    }

    &>form {
      background-color: #ffffff;
      margin-block: 50px;
      padding: 30px;
      display: flex;
      flex-direction: column;
      gap: 20px;

      .field {
        display: flex;
        flex-direction: column;
        gap: 6px;
      }

      textarea {
        resize: vertical;
      }

      textarea,
      input[type="text"],
      input[type="email"] {
        padding: 6px;
        border-radius: 0px;
        border-width: 1px;
        border-color: #000000;

        &:active,
        &:focus {
          outline-width: 0px;
        }
      }
    }
  }
}
</style>
  