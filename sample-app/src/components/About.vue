<template>
  <div class="holder">
    <h1>Hello {{their_name}}, this is out about page</h1>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque cursus eros sed tellus aliquet, eu laoreet lectus facilisis. Aenean at turpis aliquet, fringilla nisi sed, vestibulum ligula. Integer tincidunt pharetra tortor in fringilla. Aliquam leo tellus, maximus vitae porttitor eu, interdum et nisi. In erat metus, porta at dui sit amet, ullamcorper vulputate erat. Curabitur sagittis arcu sed feugiat condimentum. Etiam a elit ut arcu aliquet fermentum vitae a lectus.
    </p>
  </div>

</template>

<script>
export default {
  name: 'About',
  data() {
    return {
        their_name: this.$route.params.name
    }
  },
  methods: {
  }
}
</script>

<style>
.holder {
  background: #FFF;
  width: 800px;
}
</style>
