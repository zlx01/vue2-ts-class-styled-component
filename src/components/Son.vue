<template>
  <div>
    <input type="text" v-model="message" /><br />
    <div>{{ message }}</div>
    <div>{{ computedVal }}</div>
    <button @click="alert">alert</button>
    <button @click="emit">emit</button>
  </div>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue, Watch } from "vue-property-decorator";

@Component
export default class Son extends Vue {
  // props
  @Prop({ type: String, default: "default prop1 value" })
  // 用 readonly 可以保证 props 不能被修改
  // !: 表示一定会有值，这里设置了默认值
  private readonly prop1!: string;

  @Prop(Number) readonly propA: number | undefined;
  @Prop({ default: "default value" }) readonly propB!: string;
  @Prop([String, Boolean]) readonly propC: string | boolean | undefined;

  // If the name of the event is not supplied via the event argument, the function name is used instead.
  // the camelCase name will be converted to kebab-case.
  // If the return value is a promise, it is resolved before being emitted.
  @Emit("message")
  private emit() {
    // this.$emit("message", this.message);
    // 返回值作为事件参数
    return this.message;
  }

  // data
  private message = "init value";

  // computed
  get computedVal(): string {
    return this.message.split("").reverse().join("");
  }

  // watch
  @Watch("message")
  onMessageChange(val: string, oldVal: string): void {
    console.log(val, oldVal);
  }

  // life cycle hooks
  private created(): void {
    console.log("son created");
    this.message = this.prop1;
  }

  private mounted(): void {
    console.log("son mounted");
    this.init();
  }

  // methods
  private alert(): void {
    alert(this.message);
  }

  private init(): void {
    console.log("HelloWorld");
  }
}
</script>
