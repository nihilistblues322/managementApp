<template>

  <Head title="Create Students" />

  <AuthenticatedLayout>
    <template #header>
      <h2 class="text-xl font-semibold leading-tight text-gray-800">
        Create Student
      </h2>
    </template>
    <div class="py-6 mx-auto max-w-7xl sm:px-6 lg:px-8">
      <div class="lg:grid lg:grid-cols-12 lg:gap-x-5">
        <div class="space-y-6 sm:px-6 lg:px-0 lg:col-span-12">
          <form @submit.prevent="submit">
            <div class="shadow sm:rounded-md sm:overflow-hidden">
              <div class="px-4 py-6 space-y-6 bg-white sm:p-6">
                <div>
                  <h3 class="text-lg font-medium leading-6 text-gray-900">
                    Student Information
                  </h3>
                  <p class="mt-1 text-sm text-gray-500">
                    Use this form to create a new student.
                  </p>
                </div>

                <div class="grid grid-cols-6 gap-6">
                  <div class="col-span-6 sm:col-span-3">
                    <label for="name" class="block text-sm font-medium text-gray-700">Name</label>
                    <input type="text" id="name"
                      class="block w-full px-3 py-2 mt-1 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" />
                    <InputError class="mt-2" />
                  </div>

                  <div class="col-span-6 sm:col-span-3">
                    <label for="email" class="block text-sm font-medium text-gray-700">Email Address</label>
                    <input type="email" id="email" autocomplete="email"
                      class="block w-full px-3 py-2 mt-1 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" />
                    <InputError class="mt-2" />
                  </div>

                  <div class="col-span-6 sm:col-span-3">
                    <label for="class_id" class="block text-sm font-medium text-gray-700">Class</label>
                    <select id="class_id"
                      class="block w-full px-3 py-2 mt-1 bg-white border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm">
                      <option value="">
                        Select a Class
                      </option>
                      <option v-for="(item) in classes.data" :key="item.id" :value="item.id">
                        {{ item.name }}
                      </option>
                    </select>
                    <InputError class="mt-2" />
                  </div>

                  <div class="col-span-6 sm:col-span-3">
                    <label for="section_id" class="block text-sm font-medium text-gray-700">Section</label>
                    <select id="section_id"
                      class="block w-full px-3 py-2 mt-1 bg-white border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm">
                      <option value="">
                        Select a Section
                      </option>
                      <option>
                        Select a Section
                      </option>
                    </select>
                    <InputError class="mt-2" />
                  </div>
                </div>
              </div>
              <div class="px-4 py-3 text-right bg-gray-50 sm:px-6">
                <Link :href="route('students.index')"
                  class="inline-flex items-center px-4 py-2 mr-4 text-sm font-medium text-indigo-700 bg-indigo-100 border border-transparent rounded-md hover:bg-indigo-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                Cancel
                </Link>
                <button type="submit"
                  class="inline-flex justify-center px-4 py-2 text-sm font-medium text-white bg-indigo-600 border border-transparent rounded-md shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                  Save
                </button>
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
  </AuthenticatedLayout>
</template>

<script setup>
import AuthenticatedLayout from '../../Layouts/AuthenticatedLayout.vue'
import InputError from '../../Components/InputError.vue'
import { Head, Link } from '@inertiajs/vue3'
defineProps({
  classes: {
    type: Object,
    require: true
  }
})
</script>
