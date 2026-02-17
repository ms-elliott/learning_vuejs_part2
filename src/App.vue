<script setup lang="ts">
// [lang="ts"]と記述するだけでTypeScriptを使用できる様になる
// import { computed, ref} from 'vue'

// refとTypeScriptを一緒に使う
// string or number型のrefオブジェクトを定義
// const count = ref<number | string>(0)
// count.value = 'hello'

// computedとTypeScriptを一緒に使う
// const count = ref(0)
// 自動的にTypeScriptが型推論する
// const doubleCount = computed(() => {
//   if (count.value > 3) return 'hello'
//   return count.value * 2
// })
// doubleCount.value

//useTemlateRefとTypeScriptを一緒に使う
// import { onMounted, useTemplateRef } from 'vue'
// 基本的には型推論に任せる。下記のように型指定することも可能
// const userInput = useTemplateRef<HTMLElement>('user-input')
// onMounted(() => {
//   userInput.value?.focus()
// })
// userInput.value
// </script>
// <template>
//   <h1>TypeScript</h1>
//   <input ref="user-input" type="text">
// </template>


// イベントハンドラーとTypeScriptを一緒に使う
// import { computed, ref} from 'vue'

// const count = ref(0)
// const doubleCount = computed(() => {
//   if (count.value > 3) return 100
//   return count.value * 2
// })
// doubleCount.value
// イベントオブジェクトを使用する時は、型を明示的に指定する。イベント名をホバーして、payloadの右側の値をコピーし、引数に貼り付ける
// function countUp(event: PointerEvent) {
//   count.value++
//   console.log(event.clientX)
// }
// </script>
// <template>
//   <h1>TypeScript</h1>
//   <button @click="countUp">+1</button>
//   <p>count: {{ count }}</p>
// </template>

// propsとTypeScriptを一緒に使う方法
// import { ref } from 'vue'
// import ChildComp from './components/ChildComp.vue'
// const courseTitle = ref('Vue.js Course')
// </script>
// <template>
//   <h1>TypeScript</h1>
//   <ChildComp :title />
// </template>
// // ChildComp.vue
// <script setup lang="ts">

// 下記のdefinePropsの別の記述方法(分割代入)。definePropsのtitleに値が設定されてない場合は、"default course"を設定する。
// const { title = 'default course' } = defineProps<Course>()

// run time declaration
// defineProps({
//   title: {
//     // vue.jsで型指定して、受け取ることもできる
//     type: String,
//     required: true
//   }
// })
// type based declaration
// defineProps<{
//   // 型引数を指定することも可能。title?とすることで、required=falseにできる
//   title: string
// }>()
// </script>
// <template>
//   <h2>ChildComp</h2>
//   <p>title: {{ title }}</p>
// </template>

//defineModel()とTypeScriptを一緒に使う方法
// import { ref } from 'vue';
// import ChildComp from './components/ChildComp.vue'
// const userInput = ref()
// </script>
// <template>
//   <h1>TypeScript</h1>
//   <ChildComp v-model="userInput" />
//   <p>userInput: {{ userInput }}</p>
// </template>
// // ChildComp.vue
// <script setup lang="ts">
// // TypeScriptで型指定する方法
// const [model, modifiers] = defineModel<string, 'trim' | 'uppercase'>({ required: true })
// modifiers.uppercase
// // javaScriptで型指定する方法
// const model = defineModel({ type: String, required: true })
// </script>
// <template>
//   <h2>ChildComp</h2>
//   <input v-model="model" type="text">
//   <p>model: {{ model }}</p>
// </template>

// emitとtypeScriptを一緒に使う方法
// import ChildComp from './components/ChildComp.vue'
// </script>
// <template>
//   <h1>TypeScript</h1>
//   <ChildComp @update=""/>
// </template>
// // ChildComp.vue
// <script setup lang="ts">
// // defineEmits(['update'])
// defineEmits<{
//   update: [count: number]
// }>()
// </script>
// <template>
//   <h2>ChildComp</h2>
//   <button @click="$emit('update', 100)">button</button>
// </template>
