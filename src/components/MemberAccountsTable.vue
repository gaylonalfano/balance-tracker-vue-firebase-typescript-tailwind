<template>
  <div class="bg-white px-4 py-5 border-b border-gray-200 sm:px-6">
    <div
      class="-ml-4 -mt-2 flex items-center justify-between flex-wrap sm:flex-nowrap"
    >
      <div class="ml-4 mt-2">
        <h3 class="text-lg leading-6 font-medium text-gray-900">
          {{ member.name }}
        </h3>
      </div>
      <div class="ml-4 mt-2 flex-shrink-0 space-x-4">
        <button
          type="button"
          class="relative inline-flex items-center px-4 py-2 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-indigo-500 hover:bg-indigo-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
        >
          + Account
        </button>
        <button
          type="button"
          class="relative inline-flex items-center px-4 py-2 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-red-500 hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
        >
          Delete Member
        </button>
      </div>
    </div>
  </div>
  <p>Accounts will be listed here...</p>
</template>


<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "MemberAccountsTable",
  props: ["member"],
  setup(props) {
    console.log(props.member);
  },
});
</script>

<style>
</style>
