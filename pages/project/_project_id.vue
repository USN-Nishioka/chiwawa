<template>
  <div>
    <Nav></Nav>
    <div class="container mx-auto px-4 sm:px-6 lg:px-8 py-6">
      <h2 class="text-2xl font-bold leading-tight text-gray-900">{{ projectName }}のテストケース一覧</h2>
      <div class="mt-8">
        <table class="min-w-full">
          <thead>
          <tr>
            <th class="text-left py-3 px-4 uppercase font-bold text-gray-900 text-xs">ID</th>
            <th class="text-left py-3 px-4 uppercase font-bold text-gray-900 text-xs">テスト件名</th>
            <th class="text-left py-3 px-4 uppercase font-bold text-gray-900 text-xs">最新テスト</th>
            <th class="text-left py-3 px-4 uppercase font-bold text-gray-900 text-xs">最新結果</th>
          </tr>
          </thead>
          <tbody>
          <tr v-for="testCase in testCases" :key="testCase.id">
            <td class="border-t-2 border-gray-200 px-4 py-4">{{ testCase.id }}</td>
            <td class="border-t-2 border-gray-200 px-4 py-4"><router-link to="/case/99"><span class="text-blue-500">{{ testCase.title }}</span></router-link></td>
            <td class="border-t-2 border-gray-200 px-4 py-4">{{ testCase.latest_test.executed_at }} by {{ testCase.latest_test.executed_by }}</td>
            <td class="border-t-2 border-gray-200 px-4 py-4">{{ testCase.latest_test.result }}</td>
          </tr>
          </tbody>
        </table>
      </div>
    </div>
    <button @click="showCaseModal" class="fixed bottom-6 right-6 bg-green-500 text-white p-4 rounded-full shadow-lg">
      <p>+Add</p>
    </button>
    <div v-if="showModal" class="fixed z-50 top-0 left-0 w-full h-full flex items-center justify-center bg-gray-500 bg-opacity-50">
      <div class="bg-white p-4 rounded-lg shadow-lg">
        <h3 class="text-lg font-bold mb-4">テストケースを追加する</h3>
        <form>
          <div class="mb-4">
            <label class="block text-gray-700 font-bold mb-2" for="caseName">
              テストケース名
            </label>
            <input v-model="caseName" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="caseName" type="text" placeholder="テストケース名を入力してください">
          </div>
          <div class="flex items-center justify-end">
            <a @click.prevent="cancel" class="bg-gray-500 hover:bg-gray-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline mr-10">
              キャンセル
            </a>
            <button type="submit" @click.prevent="addCase" class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
              追加
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import Nav from "/components/Nav.vue";
export default {
  components: {
    Nav
  },

  data() {
    return {
      projectName: 'プロジェクトA',
      testCases: [
        {
          id: 1,
          title: 'テストケース1',
          latest_test: {
            executed_at: '2022/04/01 10:00',
            executed_by: 'John Smith',
            result: '成功'
          }
        },
        {
          id: 2,
          title: 'テストケース2',
          latest_test: {
            executed_at: '2022/04/02 11:00',
            executed_by: 'Jane Doe',
            result: '失敗'
          }
        },
        {
          id: 3,
          title: 'テストケース3',
          latest_test: {
            executed_at: '2022/04/03 12:00',
            executed_by: 'Bob Johnson',
            result: '成功'
          }
        },
        {
          id: 4,
          title: 'テストケース4',
          latest_test: {
            executed_at: '2022/04/04 13:00',
            executed_by: 'Alice Smith',
            result: '失敗'
          }
        }
      ],
      showModal: false,
      caseName: ''
    }
  },

  methods: {
    showCaseModal() {
      this.showModal = true
    },

    addCase() {
      const newCase = {
        id: this.testCases.length + 1,
        title: this.caseName,
        latest_test: {
          executed_at: '9999/12/31 00:00',
          executed_by: 'Alice Smith',
          result: '未実施'
        }
      }
      this.testCases.push(newCase)
      this.showModal = false
    },

    cancel() {
      this.showModal = false
    }
  }
}
</script>
