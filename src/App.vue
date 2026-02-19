<!-- Options API・・・vue.jsのもう1つのコンポーネントの書き方 -->
// [data, methods] Options APIでデータを操作する
<!-- <script setup lang="ts">
export default {
  data() {
    // オブジェクトを返す
    return {
      count: 0,
    }
  },
  methods: {
    countUp() {
      this.count++
    }
  }
}
</script>
<template>
  <h1>Options API</h1>
  // Composition APIでもOptions APIでもtemplateの記述方法は同じ
  <p>{{ count }}</p>
  <button @click="countUp">+1</button>
</template> -->

// [Options API] [Composition API]
<!-- [Options API]
・データの書く位置が決まっているので、何も考えなくてもある程度綺麗なコードが書ける
・リアクティビティシステムを意識する必要がない
・昔からの機能
・Composableが使えない
・TypeScriptと書き方が違い、相性が良くない
[Composition API]
・柔軟なので綺麗なコードを書くためには考える必要があるが、最適な位置にコードを置くことができる
・リアクティビティシステムを意識する必要がない
・Vue.js 3から登場
・Composableが使える
・TypeScriptと書き方がほぼ同じで、相性が良い -->

// Options APIでの [computed, watch]
<!-- <script setup lang="ts">
export default {
  data() {
    // オブジェクトを返す
    return {
      count: 0,
    }
  },
  computed: {
    doubleCount() {
      return this.count * 2
    }
  },
  watch: {
    count() {
      console.log('count watcher')
    }
  }
  methods: {
    countUp() {
      this.count++
    }
  }
}
</script>
<template>
  <h1>Options API</h1>
  // Composition APIでもOptions APIでもtemplateの記述方法は同じ
  <p>{{ count }}</p>
  <p>doubleCount: {{ doubleCount }}</p>
  <button @click="countUp">+1</button>
</template> -->

// Options APIでの [ライフサイクルフック]
<!-- <script setup lang="ts">
export default {
  data() {
    // オブジェクトを返す
    return {
      count: 0,
    }
  },
  computed: {
    doubleCount() {
      return this.count * 2
    }
  },
  watch: {
    count() {
      console.log('count watcher')
    }
  },
  // watchやmethodsと同じ階層に配置する
  mounted() {
    console.log('moumted')
  }
  methods: {
    countUp() {
      this.count++
    }
  }
}
</script>
<template>
  <h1>Options API</h1>
  // Composition APIでもOptions APIでもtemplateの記述方法は同じ
  <p>{{ count }}</p>
  <p>doubleCount: {{ doubleCount }}</p>
  <button @click="countUp">+1</button>
</template> -->

// [props, emit] コンポーネント間のデータの受け渡し
<!-- App.vue -->
<!-- <script setup lang="ts">
import ChildComp from './components/ChildComp.vue'
export default {
  components: {
    ChildComp
  },
  data() {
    return {
      parentCount: 0
    }
  }
}
</script>
<template>
  <h1>Options API</h1>
  <ChildComp :count="parentCount" @increment="parentCount++" />
</template> -->
<!-- ChildComp.vue -->
<!-- <script>
export default {
  props: {
    count: {
      type: Number,
      required: true
    }
  },
  emits: ['increment'],
  methods: {
    increment() {
      this.$emit('increment')
    }
  }
}
</script>
<template>
  <h2>ChildComp</h2>
  <p>{{ count }}</p>
  <button @click="increment">+1</button>
</template> -->

// ビルドツールを使わずにCDNからVue.jsを使う
<!-- index.html -->
<!-- // "html:5"と入力すると、HTMLの雛形が呼び出せる
// htmlをブラウザで見たい場合は、ファイルエクスプローラの当該ファイル上で右クリック->Reveal in Finder->ファイルをクリック
// vue.jsのwebサイトを開き、"CDNのVueを使用する"にあるコードをコピーし、HTMLのhead内に貼り付ける
// デプロイ(本番)の時はURLの末尾を書き換えること -->
