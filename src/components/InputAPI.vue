<template>
  <div class="inputAPI">
    <input
      type="text"
      class="inputList"
      name="inputAPI"
      @click="showProvince"
      placeholder="Chọn tỉnh thành"
    />
  </div>
</template>

<script>
export default {
  name: "InputAPI",
  props: {},
  methods: {
    showProvince() {
      this.$emit("showProvince");
    },
  },
};
</script>

<style>
input {
  padding: 0px;
}

.inputList {
  width: 470px;
  height: 48px;
  border: 1px solid #999;
  border-radius: 4px;

  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  padding-left: 10px;
}

.inputList:focus {
  border: 1px solid #007bc3;
  box-shadow: 0px 0px 8px rgba(0, 123, 195, 0.32);
  border-radius: 4px;
  outline: none;
}
</style>