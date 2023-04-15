<template>
  <div>
    <Nav></Nav>
    <div class="container mx-auto px-4 sm:px-6 lg:px-8 py-6">
      <div class="pb-5">
        <h1 class="text-3xl font-bold leading-tight text-gray-900">プロジェクトA</h1>
      </div>
      <div class="mb-8">
        <h2 class="text-2xl font-bold leading-tight text-gray-900">{{ testCase.title }}</h2>
        <div class="mt-4">
          <p class="text-gray-700">テストケースID: {{ testCase.id }}</p>
          <p class="text-gray-700">最新テスト結果: {{ testCase.latest_test.result }}</p>
          <p class="text-gray-700">実施日時: {{ testCase.latest_test.executed_at }}</p>
          <p class="text-gray-700">実施担当: {{ testCase.latest_test.executed_by }}</p>
        </div>
      </div>
      <div class="mt-8">
        <h3 class="text-xl font-bold leading-tight text-gray-900 mb-4">コメント一覧</h3>
        <div v-for="comment in testCase.comments" :key="comment.id" class="bg-white shadow overflow-hidden sm:rounded-lg mb-4">
          <div class="px-4 py-5 sm:px-6">
            <div class="flex items-center justify-between">
              <h4 class="text-lg leading-6 font-medium text-gray-900">
                {{ comment.created_by }}<span class="text-sm text-gray-500">{{ comment.created_at }}</span>
              </h4>
            </div>
            <div class="mt-2 sm:flex sm:justify-between">
              <p class="text-md text-gray-500">{{ comment.desc }}</p>
            </div>
          </div>
        </div>
      </div>
      <div class="mt-8">
        <h3 class="text-xl font-bold leading-tight text-gray-900 mb-4">テスト履歴</h3>
        <div v-for="testCache in testCase.test_caches" :key="testCache.id" class="bg-white shadow overflow-hidden sm:rounded-lg mb-4">
          <div class="px-4 py-5 sm:px-6">
            <div class="flex items-center justify-between">
              <h4 class="text-lg leading-6 font-medium text-gray-900">
                {{ testCache.executed_by }}<span class="text-sm text-gray-500">{{ testCache.executed_at }}</span>
              </h4>
            </div>
            <div class="mt-2 sm:flex sm:justify-between">
              <p class="text-md text-gray-500">{{ testCache.result }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <button @click="showResultModal" class="fixed bottom-6 right-6 bg-green-500 text-white p-4 rounded-full shadow-lg">
      <p>+Add</p>
    </button>
    <div v-if="showModal" class="fixed z-50 top-0 left-0 w-full h-full flex items-center justify-center bg-gray-500 bg-opacity-50">
      <div class="bg-white p-4 rounded-lg shadow-lg">
        <h3 class="text-lg font-bold mb-4">テスト結果を追加する</h3>
        <form>
          <div class="mb-4">
            <label class="block text-gray-700 font-bold mb-2">テスト結果</label>
            <div class="flex items-center">
              <label class="inline-flex items-center">
                <input type="radio" class="form-radio" name="result" value="成功" v-model="latestTestResult">
                <span class="ml-2">成功</span>
              </label>
              <label class="inline-flex items-center ml-6">
                <input type="radio" class="form-radio" name="result" value="失敗" v-model="latestTestResult">
                <span class="ml-2">失敗</span>
              </label>
            </div>
          </div>
          <div class="flex items-center justify-end">
            <a @click.prevent="cancel" class="bg-gray-500 hover:bg-gray-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline mr-10">
              キャンセル
            </a>
            <button type="submit" @click.prevent="addResult" class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
              追加
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import Nav from "/components/Nav";
export default {
  components: {
    Nav
  },

  data() {
    return {
      testCase: {
        id: 1,
        title: 'テストケース1',
        latest_test: {
          executed_at: '2022/04/01 10:00',
          executed_by: 'John Smith',
          result: '成功'
        },
        comments: [
          {
            id: 1,
            desc: 'このテストケースについて、以下のようなコメントがあります。',
            created_at: '2022/04/02 11:00',
            created_by: 'Jane Doe'            },
          {
            id: 2,
            desc: 'このテストケースについて、以下のようなコメントがあります。',
            created_at: '2022/04/03 12:00',
            created_by: 'Bob Johnson'
          }
        ],
        test_caches: [
          {
            id: 1,
            executed_at: '2022/04/01 10:00',
            executed_by: 'John Smith',
            result: '成功'
          },
          {
            id: 2,
            executed_at: '2022/04/02 11:00',
            executed_by: 'Jane Doe',
            result: '失敗'
          },
          {
            id: 3,
            executed_at: '2022/04/03 12:00',
            executed_by: 'Bob Johnson',
            result: '成功'
          },
          {
            id: 4,
            executed_at: '2022/04/04 13:00',
            executed_by: 'Alice Smith',
            result: '失敗'
          }
        ]
      },
      showModal: false,
      resultName: '',
      latestTestResult: ''
    }
  },

  methods: {
    showResultModal() {
      this.showModal = true
    },

    addResult() {
      const newResult = {
        //
      }
      this.showModal = false
    },

    cancel() {
      this.showModal = false
    }
  }
}
</script>

