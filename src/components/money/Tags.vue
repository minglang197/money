<template>
  <div class="tags">
    <ul class="current">
      <li>衣</li>
      <li>食</li>
      <li>住</li>
      <li>行</li>
      <li>行</li>
      <li>行</li>
      <li>行</li>
      <li>行</li>
    </ul>
    <div class="new">
      <button>新增标签</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Tags",
};
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