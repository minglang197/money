<template>
  <nav>
    <Layout class-prefix="layout">
      <NumberPad
        @update:value="onUpdateAmount"
        @submit="saveRecord"
      ></NumberPad>
      <Notes @update:value="onUpdateNotes"></Notes>
      <Tags :data-source.sync="tags" @update:value="onUpdateTags"></Tags>
      <Types :value.sync="record.type"></Types>
    </Layout>
  </nav>
</template>



<script lang="ts">
import Vue from "vue";
import NumberPad from "@/components/money/NumberPad.vue";
import Notes from "@/components/money/Notes.vue";
import Types from "@/components/money/Types.vue";
import Tags from "@/components/money/Tags.vue";
import { Component, Watch } from "vue-property-decorator";

window.localStorage.setItem("version", "0.01");

type Record = {
  tags: string[];
  notes: string;
  type: string;
  amount: number; //给四个组件设置类型
  createdAt: Date | undefined;
};
@Component({ components: { NumberPad, Tags, Types, Notes } })
export default class Money extends Vue {
  tags = ["衣", "食", "住", "行", "干饭"];
  recordList: Record[] = JSON.parse(
    window.localStorage.getItem("recordList") || "[]"
  );
  record: Record = {
    tags: [],
    notes: "",
    type: "-",
    amount: 0,
    createdAt: undefined,
  };
  //给四个组件设置初始值
  //给四个组件传递初始值，在组件中看

  onUpdateTags(value: string[]) {
    this.record.tags = value;
  }
  onUpdateNotes(value: string) {
    this.record.notes = value;
  }
  onUpdateAmount(value: string) {
    this.record.amount = parseFloat(value);
  }
  saveRecord() {
    const deepClone: Record = JSON.parse(JSON.stringify(this.record));
    this.recordList.push(deepClone);
    deepClone.createdAt = new Date();
  }
  @Watch("recordList")
  onRecordListChange() {
    window.localStorage.setItem("recordList", JSON.stringify(this.recordList));
  }
}
</script>


<style lang="scss">
.layout-content {
  display: flex;
  flex-direction: column-reverse;
}
</style>