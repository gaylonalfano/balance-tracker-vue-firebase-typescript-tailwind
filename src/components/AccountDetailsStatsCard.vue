<template>
  <dl class="mt-5 grid grid-cols-1 gap-5 sm:grid-cols-3">
    <div
      v-for="account in member.accounts"
      :key="account.type"
      class="bg-white overflow-hidden shadow rounded-lg"
    >
      <div class="px-4 py-5 sm:p-6">
        <dt class="text-sm font-medium text-gray-500 truncate">
          {{ account.type }}
        </dt>
        <dd
          class="flex items-baseline mt-1 text-3xl font-semibold text-gray-900"
        >
          ¥{{ account.balance }}
          <div
            class="ml-2 flex items-baseline text-sm font-semibold text-green-600"
          >
            <svg
              class="self-center flex-shrink-0 h-5 w-5 text-green-500"
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
          <!-- Add Transaction Router Link -->
          <div class="ml-auto text-sm">
            <router-link
              :to="{
                name: 'AddTransaction',
                params: { id: member.id, type: account.type },
              }"
              class="font-medium text-indigo-600 hover:text-indigo-500"
            >
              Edit
            </router-link>
          </div>
        </dd>
      </div>
    </div>
  </dl>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "AccountDetailsStatsCard",
  props: ["member"],
  setup(props) {
    console.log("AccountDetailsStatsCard");
    // Q: Can I retrieve enough info to reroute to AddTransaction?
    // I do have props.member.id, props.member.accounts, {{ account.type }}
    // A: Yes! pass in params: { id: member.id, type: account.type }
    console.log(props.member);
    console.log("accounts", props.member.accounts);
  },
});
</script>

<style>
</style>

