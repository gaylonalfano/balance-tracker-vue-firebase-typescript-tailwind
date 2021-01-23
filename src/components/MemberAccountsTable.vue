<template>
  <div class="bg-white px-4 py-5 sm:px-6">
    <div
      class="-ml-4 -mt-2 flex items-center justify-between flex-wrap sm:flex-nowrap"
    >
      <div class="ml-4 mt-2">
        <h3 class="text-lg leading-6 font-medium text-gray-900">
          {{ member.name }}--{{ member.id }}
        </h3>
      </div>
      <div class="ml-4 mt-2 flex-shrink-0 space-x-4">
        <button
          @click="handleDeleteMember"
          type="button"
          class="inline-flex items-center p-1 border border-transparent rounded-full shadow-sm text-white bg-red-500 hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
        >
          <svg
            class="w-5 h-5"
            fill="currentColor"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M20 12H4"
            ></path>
          </svg>
        </button>
      </div>
    </div>
  </div>
  <!-- Table header and rows -->
  <div class="flex flex-col">
    <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
      <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
        <div
          class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg"
        >
          <table class="min-w-full divide-y divide-gray-200">
            <AccountDetailsHeader />
            <AccountDetailsRow :accounts="member.accounts" />
          </table>
        </div>
      </div>
    </div>
  </div>
</template>


<script lang="ts">
import { defineComponent, ref } from "vue";
import AddAccount from "@/components/AddAccount.vue";
import AccountDetailsHeader from "@/components/AccountDetailsHeader.vue";
import AccountDetailsRow from "@/components/AccountDetailsRow.vue";
import useDocument from "@/composables/useDocument";

export default defineComponent({
  name: "MemberAccountsTable",
  components: { AddAccount, AccountDetailsHeader, AccountDetailsRow },
  props: ["member"],
  setup(props) {
    // We already have the member object via props. Let's pull in useDocument()
    // so we can update the accounts property (Array of Maps)
    const { updateDoc, deleteDoc, error } = useDocument(
      "members",
      props.member.id
    );

    // Let's delete member docs
    async function handleDeleteMember() {
      // We already have selected our document via useDocument('members', props.member.id)
      // Just need to delete it.
      await deleteDoc();

      // Q: Need to reroute or anything? Let's test...
    }

    return { error, handleDeleteMember };
  },
});
</script>

<style>
</style>
