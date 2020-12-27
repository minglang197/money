<template>
  <div>
    <label class="notes">
      <span class="name">备注</span>
      <input type="text" placeholder="在这里输入备注" v-model="value" />
    </label>
  </div>
</template>


<script lang="ts">
import Vue from "vue";
import { Component, Watch } from "vue-property-decorator";
@Component
export default class Notes extends Vue {
  value = "";
  @Watch("value")
  onValueChange(value: string) {
    this.$emit("update:value", value);
  }//value的值变化的时候把值传给父组件money上
}
</script>


<style lang="scss" scoped>
.notes {
  font-size: 14px;
  background-color: #f5f5f5;
  padding-left: 16px;
  display: flex;
  align-items: center;
  .name {
    padding-right: 16px;
  }
  input {
    height: 50px;
    flex-grow: 1;
    background-color: transparent;
    border: none;
    padding-left: 15px;
  }
}
</style>