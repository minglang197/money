<template>
  <nav>
    <router-link to="/money" class="item" active-class="selected">
      <Icons name="money" />
      记账
    </router-link>
    <router-link to="/labels" class="item" active-class="selected">
      <Icons name="labels" />
      标签
    </router-link>
    <router-link to="/statistics" class="item" active-class="selected">
      <Icons name="statistics" />
      统计
    </router-link>
  </nav>
</template>

<script lang ="ts">
export default {
  name: "Nav",
};
</script>

<style lang="scss" scoped>
@import "~@/assets/style/helper.scss";
nav {
  display: flex;
  flex-direction: row;
  font-size: 12px;
  box-shadow: 0 0 4px #cccccc;
  > .item {
    padding: 2px 0 0 0;
    color: black;
    width: 33.3333%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    .icon {
      width: 32px;
      height: 32px;
    }
  }
  > .item.selected {
    color: $color-heightlight;
  }
}
</style>