<template>
  <Form  class=' form'  @submit="formSubmit" :validation-schema="simpleSchema">
    <div class="form-block form-block-name">
      <Field :validateOnBlur="false" class="form-input" v-model="name"  name="name" type="text" placeholder="Enter your name" ></Field>
      <ErrorMessage class="form-error" name="name"></ErrorMessage>

    </div>
    <div class="form-block form-block-phone">
      <Field :validateOnBlur="false" class="form-input" v-model="phone" name="phone" type="text" placeholder="Enter your phone"></Field>
    <ErrorMessage class="form-error"  name="phone"></ErrorMessage>
    </div>
    <MobileButton :disabled="loading" :class="{ 'submitting': loading }" class=" form-submit form-submit__mobile" type="submit">Call me back</MobileButton>
    <PrimaryButton :disabled="loading" :class="{ 'submitting': loading }" class=" form-submit form-submit__desktop" type="submit">Call me back</PrimaryButton>
  </Form>
</template>

<script>


import {Form, Field, ErrorMessage} from 'vee-validate'
import MobileButton from '../MobileButton/MobileButton.vue';
import PrimaryButton from '../PrimaryButton/PrimaryButton.vue';



export default {
  data: () => ({
    name: '',
    phone: '',
    loading: false,
    simpleSchema: {
      name(someValue) {
        if(!someValue) return 'This field is required'
        return true
      },
      phone(someValue){
        if(!someValue) return 'This field is required'
        return true
      }
    }
  }),

  components: {
    Form,
    Field,
    ErrorMessage,
    MobileButton,
    PrimaryButton
  },
  methods: {
    validateRequired(value) {
      if(!value) return 'This field is required'
      return true
    },
    formSubmit(values, actions){
      this.loading = true
      let formData = new FormData();
      formData.append('name', values.name)
      formData.append('phone', values.phone)
      actions.resetForm();
      // fetch(`http://sub.restor.server/wp-admin/admin-ajax.php?action=restormail`, {
      fetch("https://admin.restor-chicago.com/wp-admin/admin-ajax.php?action=restormail", {
        method: 'POST',
        body: formData
      })
      .then(() => {
        this.loading = false;
        actions.resetForm();
        this.$router.push({name: 'Thanks'})
      })
      .catch(() => {
        this.loading = false;
        actions.resetForm();
        this.$router.push({name: 'Thanks'})
      })
      .finally(()=> {

        // this.$router.push({name: 'Thanks'})
      })
      // this.$router.push({name: 'Thanks'})
    }
  }
}
</script>

<style>

</style>