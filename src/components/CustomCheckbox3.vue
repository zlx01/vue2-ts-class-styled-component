<template>
  <input type="checkbox" v-model="checkedValue" />
</template>

<script lang="ts">
import { Component, ModelSync, Vue } from "vue-property-decorator";

@Component
export default class CustomCheckbox1 extends Vue {
  @ModelSync("checked", "change", { type: Boolean })
  private checkedValue!: boolean;
}
</script>

<style scoped></style>
