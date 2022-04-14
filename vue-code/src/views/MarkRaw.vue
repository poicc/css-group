<template>
  <div class="mark">
    你好 {{ obj.name }}
    <button @click="update">不能修改数据</button>
  </div>
</template>

<script>
// markRaw

// import { markRaw } from "vue";
// export default {
//   data: () => ({
//     obj: markRaw({ name: "Vue" }),
//   }),
//   methods: {
//     update() {
//       this.obj.name = "Ken";
//       console.log(this.obj);
//     },
//   },
// };

// readonly
import { readonly } from 'vue'
export default {
  data: () => ({
      obj: readonly({ name: "Vue" })
  }),
  methods: {
    update(){
      this.obj.name = 'Ken'
      console.log(this.obj)
    }
  }
}
</script>



<style>
.mark {
  background-color: #d0d0d0;
  height: 400px;
}
</style>