<template>
  <div class="resultProvince">
    <div  class="result">

      <div v-for="provinceSelect in selected" :key="provinceSelect.name" class="result__item">
        <p>{{ provinceSelect }}</p>
        <img @click="deleteProvince(provinceSelect)" src="../assets/close.png" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "resultProvince",
  props: {
    selected: {
      Array
    },
    // props ko thay đổi
    
  },
  computed: {
    // result() {
    //   return this.selected.length;
    // },
  },
  methods: {
    deleteProvince(provinceSelect) {

        this.$emit("deProvSelected", provinceSelect)
        
      },
  },
};
</script>

<style>
.result {
  display: relative;
  border: 1px solid #999999;
  margin-top: 8px;
  min-height: 48px;
  width: 480px;
  cursor: pointer;
  align-items: center;
  border-radius: 4px;

  display: flex;
  flex-wrap: wrap;
}

.result__item {
  position: relative;
  max-width: 199px;
  min-height: 32px;
  background-color: #f8f8f8;
  border-radius: 32px;

  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  margin: 8px 4px 8px 8px;
}

.result__item p {
  /* line-height: 24px; */
  color: #333333;
  margin: 0px 0px 0px 16px;
}

/* close button */
.result img {
  width: 11px;
  height: 11px;
  margin: 0px 11px 0px 11px;
}
</style>