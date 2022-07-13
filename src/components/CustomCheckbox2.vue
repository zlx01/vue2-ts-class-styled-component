<template>
  <input
    type="checkbox"
    :checked="checked"
    @change="$emit('change', $event.target.checked)"
  />
</template>

<script lang="ts">
import { Component, Model, Vue } from "vue-property-decorator";

@Component
export default class CustomCheckbox1 extends Vue {
  @Model("change", { type: Boolean })
  private readonly checked!: boolean;
}
</script>

<style scoped></style>
