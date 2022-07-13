<template>
  <div>
    <Father></Father>
    <hr />
    <custom-input1 v-model="searchText1"></custom-input1>
    <custom-input2 v-model="searchText2"></custom-input2>
    <custom-input3 :searchText.sync="searchText3"></custom-input3>
    <hr />
    <custom-checkbox1 v-model="checkObj.checked1"></custom-checkbox1>
    <custom-checkbox2 v-model="checkObj.checked2"></custom-checkbox2>
    <custom-checkbox3 v-model="checkObj.checked3"></custom-checkbox3>
    <hr />
    <VModelTest v-model="name"></VModelTest>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from "vue-property-decorator";
import Father from "@/components/Father.vue";
import CustomInput1 from "@/components/CustomInput1.vue";
import CustomInput2 from "@/components/CustomInput2.vue";
import CustomInput3 from "@/components/CustomInput3.vue";
import CustomCheckbox1 from "@/components/CustomCheckbox1.vue";
import CustomCheckbox2 from "@/components/CustomCheckbox2.vue";
import CustomCheckbox3 from "@/components/CustomCheckbox3.vue";
import VModelTest from "@/components/VModelTest.vue";

@Component({
  components: {
    Father,
    CustomInput1,
    CustomInput2,
    CustomInput3,
    CustomCheckbox1,
    CustomCheckbox2,
    CustomCheckbox3,
    VModelTest,
  },
})
export default class Foo extends Vue {
  searchText1 = "我的秘密又托付给谁呢";
  searchText2 = "道不同，不相为谋";
  searchText3 = "最伟大的作品";

  checkObj = {
    checked1: true,
    checked2: false,
    checked3: true,
  };
  name = "王大锤";

  @Watch("searchText1")
  onSearchText1Change(val: string, oldVal: string): void {
    console.log("searchText1", val);
  }

  @Watch("searchText2")
  onSearchText2Change(val: string, oldVal: string): void {
    console.log("searchText2", val);
  }

  @Watch("searchText3")
  onSearchText3Change(val: string, oldVal: string): void {
    console.log("searchText3", val);
  }

  @Watch("checkObj", { deep: true, immediate: false })
  onChecked1Change(val: boolean, oldVal: boolean): void {
    console.log("checkObj", JSON.stringify(val));
  }

  @Watch("name")
  onNameChange(val: string, oldVal: string): void {
    console.log("name", val);
  }
}
</script>
