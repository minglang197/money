<template>
  <div>
    <ul class="types">
      <li :class="value === '-' && 'selected'" @click="selectType('-')">支出</li>
      <li :class="value === '+' && 'selected'" @click="selectType('+')">收入</li>
    </ul>
  </div>
</template>


<script lang="ts">
import Vue from "vue";
import { Component, Prop } from "vue-property-decorator";

@Component
export default class Types extends Vue {
  // type = "-";
  @Prop({ default: "-" }) readonly value!: string;
  //初始值
  selectType(value: string) {
    if (value !== "-" && value !== "+") {
      throw new Error("value is unknow");
    }
    this.$emit("update:value", value);
    // this.type = type;
  } //父组件传值时删除这些watch
  // @Watch("type")
  // onTypeChange(value: string) {
  //   this.$emit("update:value", value);
  // }
}
</script>

<style lang="scss" scoped>
.types {
  background-color: #fac054;
  display: flex;
  font-size: 24px;
  li {
    display: flex;
    width: 50%;
    height: 64px;
    justify-content: center;
    align-items: center;
    position: relative;
    &.selected::after {
      content: "";
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 2px;
      background-color: #333;
    }
  }
}
</style>