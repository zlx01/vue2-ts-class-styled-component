<template>
  <input type="text" v-model="_value" />
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class CustomInput2 extends Vue {
  @Prop({ type: String, default: "" })
  private value!: string;

  get _value(): string {
    return this.value;
  }

  set _value(val: string) {
    this.$emit("input", val);
  }
}
</script>

<style scoped></style>
