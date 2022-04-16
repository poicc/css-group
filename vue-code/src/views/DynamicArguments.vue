<template>
  <div class="dynamic-arguments">
    <h2>
      模板插值
      <br />
      <input v-model="msg" type="text" />
      <br />
      {{ msg }}
    </h2>
    <br />

    <h2>
      JavaScript 表达式
      <br />
      字符串 split 操作：{{ msg.split(",")[0] }}
      <br />
      数值计算：{{ num }}
      <br />
      数组操作：{{ arr[0] }}
    </h2>
    <br />

    <h2>
      v-bind: 绑定属性
      <br />
      <a :[urlKey]="a">github.com</a>
    </h2>
    <br />

    <h2>
      v-on:[handlerEventName] 绑定事件名变量
      <br />

      <!-- v-on:[handlerEventName] 绑定事件名变量 -->
      <button v-on:click="increase">{{ num }}</button>

      <!-- 使用变量来定义事件名字 -->
      <button v-on:[clickEventName]="increase">{{ num }}</button>

      <!-- 简写，提高效率，减少代码量 -->
      <button @[clickEventName]="increase">{{ num }}</button>
    </h2>
    <br />
    <h2>
      v-slot:[slotName] 具名插槽
      <parent>
        <!-- <template v-slot:child> -->

        <!-- 使用 ref定义一个响应式变量 child -->
        <template v-slot:[child]>
          <child></child>
        </template>
      </parent>
    </h2>

    <h2>
      #[slotName] 简写模式
      <parent>
        <template #[child]>
          <child></child>
        </template>
      </parent>
    </h2>
  </div>
</template>

<script>
import { ref } from "vue";

import parent from "./bbb";
import child from "./aaa";

export default {
  name: "DynamicArguments",
  components: {
    parent,
    child,
  },
  setup() {
    let msg = ref("模板插值1,模板插值2,模板插值3");

    let num = ref(5);

    // 使用变量来定义事件名字
    let clickEventName = ref("click");

    let arr = ref(["YG.", "前端开发", "Python100天"]);

    let a = ref("github.com");

    let urlKey = ref("href");

    const increase = () => {
      num.value++;
    };

    let child = ref("child");
    return {
      msg,
      num,
      arr,
      a,
      urlKey,
      increase,
      clickEventName,
      child,
    };
  },
};
</script>

<style scoped>
input {
  width: 300px;
}
</style>
