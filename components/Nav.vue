<template>
  <nav class="bg-green-500">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        <div class="flex-shrink-0">
          <h1 class="text-white text-3xl font-bold">テストケース管理システム</h1>
        </div>
        <div class="hidden md:block">
          <div class="ml-4 flex items-center md:ml-6">
            <router-link class="text-white hover:text-gray-300 px-3 py-2 rounded-md text-sm font-medium" to="/projects">プロジェクト一覧</router-link>
            <router-link class="text-white hover:text-gray-300 px-3 py-2 rounded-md text-sm font-medium" to="/">ログアウト</router-link>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
}
</script>
