<template>
  <Header />
  <Form />
  <Footer />
</template>

<script>
import { defineComponent } from 'vue'
import Header from './components/Header.vue'
import Form from './components/Form.vue'
import Footer from './components/Footer.vue'


export default {
  name: 'App',
  components: {
    Header,
    Form,
    Footer,
  },
}
</script>
