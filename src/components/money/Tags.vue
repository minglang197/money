<template>
  <div class="tags">
    <ul class="current">
      <li
        v-for="tag in dataSource"
        :key="tag"
        @click="toggle(tag)"
        :class="{ selected: selectedTags.indexOf(tag) >= 0 }"
      >
        {{ tag }}
      </li>
    </ul>
    <div class="new">
      <button @click="create">新增标签</button>
    </div>
  </div>
</template>
<script lang="ts">
import Vue from "vue";
import { Component, Prop } from "vue-property-decorator";
@Component
export default class Tags extends Vue {
  @Prop() readonly dataSource: string[] | undefined;
  selectedTags: string[] = [];
  toggle(tag: string) {
    const index = this.selectedTags.indexOf(tag);
    if (index >= 0) {
      this.selectedTags.splice(index, 1);
    } else {
      this.selectedTags.push(tag);
    }
    this.$emit("update:value", this.selectedTags);
  }
  create() {
    const name = window.prompt("请输入标签名");
    if (name === "") {
      window.alert("请输入正确的标签名");
    } else if (this.dataSource) {
      this.$emit("update:dataSource", [...this.dataSource, name]);
    }
  }
}
</script>

<style lang="scss" scoped>
.tags {
  flex-grow: 1;
  font-size: 14px;
  padding: 16px;
  .current {
    display: flex;
    flex-wrap: wrap;
    li {
      background-color: #d9d9d9;
      height: 24px;
      border-radius: (24px/2);
      padding: 0 16px;
      margin-right: 11px;
      line-height: 24px;
      margin-top: 5px;
      &.selected {
        background: #fac054;
      }
    }
  }
  .new {
    padding-top: 16px;
    button {
      background-color: transparent;
      border: none;
      color: #999999;
      padding: 0 4px;
      border-bottom: 1px solid;
    }
  }
}
</style>