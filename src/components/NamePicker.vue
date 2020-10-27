<template>
  <div>
    <label>Введите имя</label>
    <b-input-group>
      <b-form-input v-model="pickedName"></b-form-input>
      <b-input-group-append>
        <b-button variant="success" v-on:click="saveName">Сохранить</b-button>
      </b-input-group-append>
    </b-input-group>
  </div>
</template>

<script>
export default {
  name: "NamePicker",
  data() {
    return  {
      pickedName: '',
    }
  },
  methods: {
    saveName(evt) {
      evt.preventDefault();
      let date = new Date(Date.now() + 86400e3);
      date = date.toUTCString();
      document.cookie = "name=" + this.pickedName + "; expires=" + date;
      this.$emit('hide', this.pickedName);
    }
  }
}
</script>

<style scoped>

</style>