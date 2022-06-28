<template>
  <div class="provinceList">
    <div class="crollList">
      <div v-for="provinceApi in dataAPI" :key="provinceApi">
        <label class="option container">
          <input
            type="checkbox"
            :value="provinceApi.name"
            v-model="listChecked"
            @input="hidenShow(provinceApi)"
          />
          <span class="checkmark"></span>
          {{ provinceApi.name }}
        </label>
      </div>
      <div class="button">
        <button @click="acceptSelect" class="button__accept">Đồng ý</button>
        <button @click="cancelSelect" class="button__cancel">Hủy</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "provinceList",
  props: {
    dataAPI: Array,
    modelValue: Array,
  },

  data() {
    return {
      listChecked: [],
    };
  },
  watch: {
    modelValue: {
      handler(val) {
        this.listChecked = val;
      },
      immediately: true,
    },
    listChecked(val) {
      this.$emit("input", val);
    },
  },
  methods: {
    cancelSelect() {
      (this.listChecked = []),
       this.$emit("resetSelected",
        this.listChecked);
    },

    hidenShow(provinceApi) {
      this.$emit("handleShow", provinceApi.name);
      console.log(provinceApi);
    },
    acceptSelect() {
      this.$emit("showSelected");
    },
  },
};
</script>

<style>
.provinceList {
  margin: auto;
  width: 100%;

  height: 304px;
  align-items: center;
  background: #ffffff;
  position: relative;
  box-shadow: 0px 1px 8px rgba(102, 102, 102, 0.2);
}
.list-main {
  overflow-y: scroll;
  height: 304px;
}
.crollList {
  overflow-y: scroll;
  height: 304px;
}
::-webkit-scrollbar {
  width: 8px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #dcdcdc;
  border-radius: 6px;
}
.option {
  display: block;
  line-height: 10px;
  padding: 8px 0px;
}

.option:hover {
  background-color: #e7f1fd;
}
.button {
  position: absolute;
  bottom: 0px;
  background-color: #fff;
  display: block;
  width: 100%;

  padding: 8px 0px 16px 16px;
}

.button__accept {
  /* margin-top: 10px; */

  background-color: #007bc3;
  color: #fff;
  padding: 4px 19px;
  outline: none;
  border: 0px;
  border-radius: 4px;
  font-weight: 700;
  font-size: 16px;

  font-weight: 700;
  height: 32px;
  width: 104px;
}

input {
  padding-left: 19px;
}

.button__cancel {
  border: 0px;
  background-color: #fff;
  color: #007bc3;
  font-weight: 400;
  font-size: 16px;
  width: 82px;
  height: 24px;
}

/* Custom checkbox */
/* The container */
.container {
  display: block;
  position: relative;
  padding: 0px 0px 0px 48px;
  line-height: 40px;
  margin-bottom: 0;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default checkbox */
.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 11px;
  left: 19px;
  height: 18px;
  width: 18px;
  background-color: #eee;
}

/* On mouse-over, add a grey background color */
.container:hover input ~ .checkmark {
  background-color: #ccc;
}

/* When the checkbox is checked, add a blue background */
.container input:checked ~ .checkmark {
  background-color: #45d1c9;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.container input:checked ~ .checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.container .checkmark:after {
  left: 4px;
  top: 2px;
  width: 6px;
  height: 8px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
</style>