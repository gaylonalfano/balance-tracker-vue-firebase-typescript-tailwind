<template>
  <dl class="mt-5 grid grid-cols-1 gap-5 sm:grid-cols-2 lg:grid-cols-3">
    <div
      v-for="account in member.accounts"
      :key="account.type"
      class="flex flex-col bg-white overflow-hidden shadow rounded-lg"
    >
      <div class="flex-grow px-4 py-5 sm:p-6">
        <div class="flex items-center">
          <div class="ml-5 w-0 flex-1">
            <dt class="text-sm font-medium text-gray-500 truncate">
              {{ account.type }}
            </dt>
            <dd class="flex items-baseline">
              <div class="text-2xl font-semibold text-gray-900">
                ¥{{ account.balance }}
              </div>
              <!-- Latest Transaction Arrow Indicator -->
              <div
                v-if="account.latestTransactionAmount > 0"
                class="ml-2 flex items-baseline text-sm font-semibold text-green-600"
              >
                <svg
                  class="self-center flex-shrink-0 w-5 h-5 text-green-500"
                  fill="currentColor"
                  viewBox="0 0 20 20"
                  aria-hidden="true"
                >
                  <path
                    fill-rule="evenodd"
                    d="M5.293 9.707a1 1 0 010-1.414l4-4a1 1 0 011.414 0l4 4a1 1 0 01-1.414 1.414L11 7.414V15a1 1 0 11-2 0V7.414L6.707 9.707a1 1 0 01-1.414 0z"
                    clip-rule="evenodd"
                  />
                </svg>
                <span class="sr-only"> Increased by </span>
                {{ account.latestTransactionAmount }}
              </div>
              <div
                v-else
                class="flex items-baseline ml-2 text-sm font-semibold text-red-600"
              >
                <svg
                  class="self-center flex-shrink-0 w-5 h-5 text-red-500"
                  fill="currentColor"
                  viewBox="0 0 20 20"
                  aria-hidden="true"
                >
                  <path
                    fill-rule="evenodd"
                    d="M14.707 10.293a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 111.414-1.414L9 12.586V5a1 1 0 012 0v7.586l2.293-2.293a1 1 0 011.414 0z"
                    clip-rule="evenodd"
                  />
                </svg>
                <span class="sr-only"> Decreased by </span>
                {{ account.latestTransactionAmount }}
              </div>
            </dd>
          </div>
        </div>
      </div>
      <!-- Bottom footer section of card -->
      <div class="bg-gray-50 px-4 py-4 sm:px-6">
        <div class="flex justify-between text-sm">
          <!-- Add Transaction Router Link -->
          <router-link
            :to="{
              name: 'AddTransaction',
              params: { id: member.id, type: account.type },
            }"
            class="font-medium text-indigo-600 hover:text-indigo-500"
          >
            Edit
          </router-link>
          <!-- View Transactions Router Link -->
          <router-link
            :to="{
              name: 'Dashboard',
              params: { id: member.id, type: account.type },
            }"
            class="font-medium text-gray-600 hover:text-gray-500"
          >
            View
          </router-link>
          <!-- Delete Account -->
          <router-link
            :to="{
              name: 'DeleteAccount',
              params: { id: member.id, type: account.type },
            }"
            class="font-medium text-red-600 hover:text-red-500"
          >
            Delete
          </router-link>
        </div>
      </div>
    </div>
  </dl>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import DeleteAccountModal from "@/views/DeleteAccountModal.vue";

export default defineComponent({
  name: "AccountDetailsStatsCard",
  components: { DeleteAccountModal },
  props: ["member"],
});
</script>

<style>
</style>

