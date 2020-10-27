<template>
  <div class="content">
    <h2>Генератор комплиментов девушке</h2>
    <NamePicker v-show="show" @hide="hide" />
    <ComplimentPicker v-show="!show" :pickedName="pickedName"/>
  </div>
</template>

<script>
import NamePicker from "@/components/NamePicker";
import ComplimentPicker from "@/components/ComplimentPicker";

export default {
  name: 'Home',
  components: {
    ComplimentPicker,
    NamePicker
  },
  data() {
    return {
      show: true,
      pickedName: ''
    }
  },
  methods: {
    hide(val) {
      this.show = false;
      this.pickedName = val;
    }
  },
  mounted() {
    let name = document.cookie || 0;
    if (name) {
      name = name.match(/name=\W+/gm);
      name = name[0].replace('name=', '');
      this.show = false;
      this.pickedName = name;
    }
  }
}
</script>

<style lang="scss">
.content {
  min-width: 400px;
  margin: auto;
}

</style>
