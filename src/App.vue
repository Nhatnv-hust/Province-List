<template>
  <div class="app">
    <InputAPI @showProvince="showProvince" />
    <Provincelist
      :dataAPI="callProvince"
      v-model="selected"
      @handleShow="handleShow"
      v-show="showProv"
      @showSelected="showSelected"
      @resetSelected="resetSelected"
    />
    <!--{ v-mode="selected" viết tắt 2 hàm 
          1, :model="selecte"
          2   @input = $even.target.value } -->
    <Result
      :selected="selected"
      v-show="!showProv"
      @deProvSelected="deProvSelected"
    />
  </div>
</template>

<script>
import axios from "axios";
import InputAPI from "./components/InputAPI.vue";
import Provincelist from "./components/Provincelist.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  data() {
    return {
      callProvince: [],
      selected: [],
      showProv: true,
    };
  },
  created() {
    axios
      .get("https://provinces.open-api.vn/api/")
      .then((response) => (this.callProvince = response.data));
  },

  components: {
    InputAPI,
    Provincelist,
    Result,
  },
  methods: {
    resetSelected(e) {
      this.selected = e;
    },
    deProvSelected(e) {
      this.selected = this.selected.filter((value) => value !== e);
    },
    showSelected() {
      this.showProv = !this.showProv;
    },
    showProvince() {
      this.showProv = !this.showProv;
    },
    handleShow(e) {
      const index = this.selected.indexOf(e);
      if (index == -1) {
        this.selected.push(e);
      } else {
        this.selected.splice(index, 1);
      }
    },
  },
};
</script>

<style>
#app {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Noto Sans", sans-serif;
  margin: auto;
  width: 480px;
  box-sizing: border-box;
}
</style>
