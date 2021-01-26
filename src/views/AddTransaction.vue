<template>
  <!-- This example requires Tailwind CSS v2.0+ -->
  <div class="fixed z-10 inset-0 overflow-y-auto">
    <div
      class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0"
    >
      <!--
      Background overlay, show/hide based on modal state.

      Entering: "ease-out duration-300"
        From: "opacity-0"
        To: "opacity-100"
      Leaving: "ease-in duration-200"
        From: "opacity-100"
        To: "opacity-0"
    -->
      <div class="fixed inset-0 transition-opacity" aria-hidden="true">
        <div class="absolute inset-0 bg-indigo-50 opacity-75"></div>
      </div>

      <!-- This element is to trick the browser into centering the modal contents. -->
      <span
        class="hidden sm:inline-block sm:align-middle sm:h-screen"
        aria-hidden="true"
        >&#8203;</span
      >
      <!--
      Modal panel, show/hide based on modal state.

      Entering: "ease-out duration-300"
        From: "opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
        To: "opacity-100 translate-y-0 sm:scale-100"
      Leaving: "ease-in duration-200"
        From: "opacity-100 translate-y-0 sm:scale-100"
        To: "opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
    -->
      <div
        class="inline-block align-bottom bg-white rounded-lg px-4 pt-5 pb-4 text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full sm:p-6"
        role="dialog"
        aria-modal="true"
        aria-labelledby="modal-headline"
      >
        <div>
          <div class="mt-3 text-center sm:mt-5">
            <h3
              class="text-lg leading-6 font-medium text-gray-900"
              id="modal-headline"
            >
              Add transaction id:{{ id }} -- type:{{ type }}
            </h3>
            <div class="mt-2 flex justify-center">
              <form @submit.prevent="handleAddTransaction" class="space-y-6">
                <input type="hidden" name="remember" value="true" />
                <div class="rounded-md shadow-sm -space-y-px">
                  <div>
                    <label for="transaction-amount" class="sr-only"
                      >Transaction Amount</label
                    >
                    <input
                      v-model="transactionAmount"
                      id="transaction-amount"
                      name="transaction-amount"
                      type="number"
                      autocomplete="current-transaction-amount"
                      required
                      class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-t-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
                      placeholder="Transaction amount"
                    />
                  </div>
                  <div>
                    <label for="notes" class="sr-only">Notes</label>
                    <input
                      v-model="notes"
                      id="notes"
                      name="notes"
                      type="text"
                      autocomplete="notes"
                      required
                      class="appearance-none rounded-b-md relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
                      placeholder="E.g. Fortnite, etc."
                    />
                  </div>
                </div>
                <div v-if="errorAddDoc">
                  {{ errorAddDoc }}
                </div>
                <div v-if="errorUpdateDoc">
                  {{ errorUpdateDoc }}
                </div>
                <div
                  class="mt-5 sm:mt-6 sm:grid sm:grid-cols-2 sm:gap-3 sm:grid-flow-row-dense"
                >
                  <button
                    type="submit"
                    class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-indigo-600 text-base font-medium text-white hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:col-start-2 sm:text-sm"
                  >
                    Update
                  </button>
                  <button
                    @click="handleCancel"
                    type="button"
                    class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:mt-0 sm:col-start-1 sm:text-sm"
                  >
                    Cancel
                  </button>
                </div>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import { useRouter } from "vue-router";
import { timestamp } from "@/firebase/config";
import useCollection from "@/composables/useCollection";
import useDocument from "@/composables/useDocument";

export default defineComponent({
  name: "AddTransaction",
  props: ["id", "type"],
  setup(props) {
    // Q: Do I need the full member (via passing :member="member" props)?
    // Q: Or, just member.account as a props via route.params?
    // console.log(props);

    // Let's get the useCollection addDoc() functionality
    const {
      addDoc,
      error: errorAddDoc,
      isPending: isPendingAddDoc,
    } = useCollection(`members/${props.id}/transactions`);

    // Get updateDoc() functionality to add transaction.id to account transactions Array
    const {
      error: errorUpdateDoc,
      updateDoc,
      isPending: isPendingUpdateDoc,
    } = useDocument("members", props.id);

    const transactionAmount = ref<number>(0);
    const notes = ref<string>("");

    // Create new useRouter() instance to reroute to /dashboard
    // or if 'Cancel' button is clicked to go back to /dashboard
    const router = useRouter();

    function handleCancel() {
      // Go back by one record in the history (ie. to /dashboard)
      // NOTE I believe this is a full reload of dashboard which may
      // not be best UI.
      router.go(-1);
    }

    async function handleAddTransaction() {
      // Q: What is a Transaction doc going to look like? Do I have everything?
      // id, timestamp, member.id, account.type, transactionAmount, notes

      isPendingAddDoc.value = true;

      const transaction = {
        memberId: props.id,
        accountType: props.type,
        transactionAmount: transactionAmount.value,
        transactionDate: timestamp(),
        notes: notes.value,
      };
      // console.log(transaction);
      // Let's create the new doc in Transactions subcollection
      const response = await addDoc(transaction); // works!
      // console.log(response?.id);  // works!

      // Need to reset isPending
      isPendingAddDoc.value = false;

      // Confirm success, add response.id to account.transactions Array,
      // and reroute back to dashboard
      if (!errorAddDoc.value) {
        // Q: How can I retrieve the new document Id? On response?
        // A: Yep! It's on the response object! Now I can use this
        // response.id to update my account transactions Array.
        // NOTE I need to loop through member.accounts and match on type
        // Then I can simply append to its transactions Array.
        // Q: Could also update all the account properties while I'm at it?
        // Q: This is the KEY connection between accounts and transactions
        // using this data model structure.

        await updateDoc({});
      }
    }

    return {
      handleAddTransaction,
      handleCancel,
      transactionAmount,
      notes,
      errorAddDoc,
      errorUpdateDoc,
    };
  },
});
</script>

<style>
</style>
