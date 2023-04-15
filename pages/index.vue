<template>
  <div class="min-h-screen bg-gray-100 flex items-center justify-center">
    <div class="max-w-md w-full bg-white shadow-lg rounded-lg p-8">
      <div>
        <img src="logo.png" alt="logo">
      </div>
      <div class="flex items-center justify-center">
        <h2 class="text-2xl font-bold text-gray-900">chihuahua</h2>
      </div>
      <form class="mt-6" action="#" method="POST">
        <div>
          <label class="block text-gray-700 font-bold mb-2" for="username">
            ユーザー名
          </label>
          <input class="appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text" placeholder="ユーザー名を入力してください">
        </div>
        <div class="mt-4">
          <label class="block text-gray-700 font-bold mb-2" for="password">
            パスワード
          </label>
          <input class="appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="password" type="password" placeholder="パスワードを入力してください">
        </div>
        <div class="mt-6 flex justify-center">
          <nuxt-link class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="submit" to="/projects">
            ログイン
          </nuxt-link>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    login() {
      // TODO: 仮実装
    }
  }
}
</script>
