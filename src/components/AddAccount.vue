<template>
  <div>
    <div class="relative mt-4">
      <div class="absolute inset-0 flex items-center" aria-hidden="true">
        <div class="w-full border-t border-gray-300"></div>
      </div>
      <div class="relative flex justify-center">
        <button
          v-if="!showForm"
          @click="showForm = true"
          type="button"
          class="inline-flex items-center shadow-sm px-4 py-1.5 border border-gray-300 text-sm leading-5 font-medium rounded-full text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
        >
          <!-- Heroicon name: plus-sm -->
          <svg
            class="-ml-1.5 mr-1 h-5 w-5 text-gray-400"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 20 20"
            fill="currentColor"
            aria-hidden="true"
          >
            <path
              fill-rule="evenodd"
              d="M10 5a1 1 0 011 1v3h3a1 1 0 110 2h-3v3a1 1 0 11-2 0v-3H6a1 1 0 110-2h3V6a1 1 0 011-1z"
              clip-rule="evenodd"
            />
          </svg>
          <span>Account</span>
        </button>
      </div>
    </div>
    <!-- Display Add Account Form when showForm toggled -->
    <div class="flex m-auto justify-center">
      <form
        v-if="showForm"
        @submit.prevent="handleAddAccount"
        class="mt-1 space-y-4 max-w-md"
      >
        <input type="hidden" name="remember" value="true" />
        <div class="rounded-md shadow-sm -space-y-px">
          <div>
            <label for="type" class="sr-only">Account Type</label>
            <input
              v-model="type"
              id="type"
              name="type"
              type="text"
              autocomplete="type"
              required
              class="appearance-none rounded-md relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
              placeholder="Account type"
            />
          </div>
          <div>
            <label for="balance" class="sr-only">Balance</label>
            <input
              v-model="balance"
              id="balance"
              name="balance"
              type="number"
              autocomplete="balance"
              required
              class="appearance-none rounded-md relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
              placeholder="Balance"
            />
          </div>
        </div>
        <div class="flex justify-between">
          <button
            v-if="!isPending"
            class="justify-center py-2 px-4 border border-transparent text-xs font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
          >
            + Account
          </button>
          <button
            v-else
            disabled
            class="disabled cursor-not-allowed justify-center py-2 px-4 border border-transparent text-xs font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
          >
            Adding...
          </button>
          <button
            type="button"
            @click="showForm = false"
            class="justify-center py-2 px-4 border border-transparent text-xs font-medium rounded-md text-white bg-gray-500 hover:bg-gray-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
          >
            Cancel
          </button>
        </div>
        <div v-if="error">
          <h3 class="text-sm font-medium text-red-800">{{ error }}</h3>
        </div>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import { timestamp } from "@/firebase/config";
import useDocument from "@/composables/useDocument";

export default defineComponent({
  name: "AddAccount",
  props: ["member"],
  setup(props) {
    // Pull in useDocument() and the updateDoc() method
    const { updateDoc, error, isPending } = useDocument(
      "members",
      props.member.id
    );

    // Q: Where does the auth user and member come from? Parent via props?
    // A: Yes, we pass 'member' as prop from MemberAccountsTable
    // Create input data properties refs
    const type = ref<string>("");
    const balance = ref<number>(0);
    const showForm = ref<boolean>(false);

    // Handler for form submission
    async function handleAddAccount() {
      // Confirm we have user inputs for new account
      if (type.value && balance.value) {
        console.log(
          "PASSED:AddAccount:handleAddAccount:type.value && balance.value"
        );
        // Package all the inputs into an object
        // Q: Does account need to be reactive? Don't think so...
        // A: Nope.
        // NOTE Adding defaults for latestTransaction to initialize.
        const account = {
          type: type.value,
          balance: balance.value,
          latestTransactionAmount: 0,
          latestTransactionDate: "1/1/2021",
        };

        console.log("handleAddAccount:account: ", account);
        // Use our updateDoc(updatesObj) to update/add newSong
        // NOTE Don't need to do some try/catch as that's already
        // built into addDoc()!
        await updateDoc({
          // Q: Does my member doc need a pre-defined 'accounts' property? Or will it be added automatically?
          // A: YES! My spread operation below throws an Error if no 'accounts' property exists.
          // Q: How to access current/existing songs list?
          // A: Use our props! Then just spread!
          accounts: [...props.member.accounts, account],
        });

        // Collapse/hide/toggle showForm value after adding a new account
        showForm.value = false;

        // Clear form inputs
        balance.value = 0;
        type.value = "";
      }
    }
    return { handleAddAccount, type, balance, showForm, error, isPending };
  },
});
</script>

<style>
</style>
