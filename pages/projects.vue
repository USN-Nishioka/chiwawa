<template>
  <div>
    <Nav></Nav>
    <div class="container mx-auto px-4 sm:px-6 lg:px-8 py-6">
      <h2 class="text-2xl font-bold leading-tight text-gray-900">プロジェクト一覧</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mt-8">
        <div v-for="project in projects" :key="project.id">
          <div class="bg-white shadow-lg rounded-lg overflow-hidden">
            <nuxt-link to="/project/99">
              <img class="h-64 w-full object-cover object-center" :src="project.project_logo" alt="プロジェクトロゴ">
            </nuxt-link>
            <div class="p-4">
              <h3 class="text-lg font-bold text-gray-900">{{ project.project_name }}</h3>
            </div>
          </div>
        </div>
      </div>
    </div>
    <button @click="showProjectModal" class="fixed bottom-6 right-6 bg-green-500 text-white p-4 rounded-full shadow-lg">
      <p>+Add</p>
    </button>
    <div v-if="showModal" class="fixed z-50 top-0 left-0 w-full h-full flex items-center justify-center bg-gray-500 bg-opacity-50">
      <div class="bg-white p-4 rounded-lg shadow-lg">
        <h3 class="text-lg font-bold mb-4">プロジェクトを追加する</h3>
        <form>
          <div class="mb-4">
            <label class="block text-gray-700 font-bold mb-2" for="projectName">
              プロジェクト名
            </label>
            <input v-model="projectName" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="projectName" type="text" placeholder="プロジェクト名を入力してください">
          </div>
          <div class="flex items-center justify-end">
            <a @click.prevent="cancel" class="bg-gray-500 hover:bg-gray-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline mr-10">
              キャンセル
            </a>
            <button type="submit" @click.prevent="addProject" class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
              追加
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import Nav from '/components/Nav.vue'
export default {
  components: {
    Nav
  },

  data() {
    return {
      projects: [
        {
          id: 1,
          project_name: 'プロジェクトA',
          project_logo: 'https://dummyimage.com/300x200/000/fff',
        },
        {
          id: 2,
          project_name: 'プロジェクトB',
          project_logo: 'https://dummyimage.com/300x200/000/fff',
        },
        {
          id: 3,
          project_name: 'プロジェクトC',
          project_logo: 'https://dummyimage.com/300x200/000/fff',
        },
      ],
      showModal: false,
      projectName: '',
      projectLogo: ''
    }
  },
  methods: {
    showProjectModal() {
      this.showModal = true
    },

    addProject() {
      const newProject = {
        id: this.projects.length + 1,
        project_name: this.projectName,
        project_logo: 'https://dummyimage.com/300x200/000/fff',
      }
      this.projects.push(newProject)
      this.showModal = false
      this.projectName = ''
      this.projectLogo = ''
    },

    cancel() {
      this.showModal = false
    }
  }
}
</script>
