<template>
  <Navbar />
  <!-- <main class="relative z-0 flex-1 pb-8 overflow-y-auto"> -->
  <!-- Page header -->

  <header class="relative z-0 flex-1 overflow-y-auto">
    <div class="bg-white shadow">
      <div class="px-4 sm:px-6 lg:max-w-6xl lg:mx-auto lg:px-8">
        <div
          class="py-6 md:flex md:items-center md:justify-between lg:border-t lg:border-gray-200"
        >
          <div class="flex-1 min-w-0">
            <!-- Profile -->
            <div class="flex items-center">
              <img
                class="hidden w-16 h-16 rounded-full sm:block"
                src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.6&w=256&h=256&q=80"
                alt=""
              />
              <div>
                <div class="flex items-center">
                  <h1
                    class="ml-3 text-2xl font-bold text-gray-900 leading-7 sm:leading-9 sm:truncate"
                  >
                    Good morning, {{ member.name }}
                  </h1>
                </div>
              </div>
            </div>
          </div>
          <div class="flex mt-6 space-x-3 md:mt-0 md:ml-4">
            <button
              type="button"
              class="inline-flex items-center px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 shadow-sm rounded-md hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-cyan-500"
            >
              Add money
            </button>
            <button
              type="button"
              class="inline-flex items-center px-4 py-2 text-sm font-medium text-white border border-transparent shadow-sm rounded-md bg-cyan-600 hover:bg-cyan-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-cyan-500"
            >
              Send money
            </button>
          </div>
        </div>
      </div>
    </div>
  </header>

  <!-- Accounts Cards Overview -->
  <main class="bg-indigo-200 pt-8 pb-8">
    <div class="max-w-6xl px-4 mx-auto sm:px-6 lg:px-8">
      <h2 class="text-lg font-medium text-gray-900 leading-6">Overview</h2>
      <div>
        <dl class="mt-2 grid grid-cols-1 gap-5 sm:grid-cols-3">
          <div
            v-for="account in member.accounts"
            :key="account.type"
            class="overflow-hidden bg-white rounded-lg shadow"
          >
            <div class="px-4 py-5 sm:p-6">
              <dt class="text-sm font-medium text-gray-500 truncate">
                {{ account.type }}
              </dt>
              <dd class="mt-1 text-3xl font-semibold text-gray-900">
                ¥{{ account.currentBalance }}
              </dd>
            </div>
          </div>
        </dl>
      </div>
    </div>

    <h2
      class="max-w-6xl px-4 mx-auto mt-8 text-lg font-medium text-gray-900 leading-6 sm:px-6 lg:px-8"
    >
      Recent activity
    </h2>

    <!-- Activity list (smallest breakopoint only) -->
    <!-- This WILL display rows even at smallest viewport -->
    <div class="shadow sm:hidden">
      <ul
        v-for="transaction in transactions"
        :key="transaction.id"
        class="mt-2 overflow-hidden shadow divide-y divide-gray-200 sm:hidden"
      >
        <li>
          <a href="#" class="block px-4 py-4 bg-white hover:bg-gray-50">
            <span class="flex items-center space-x-4">
              <span class="flex flex-1 truncate space-x-2">
                <!-- Heroicon name: cash -->
                <svg
                  class="flex-shrink-0 w-5 h-5 text-gray-400"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                  aria-hidden="true"
                >
                  <path
                    fill-rule="evenodd"
                    d="M4 4a2 2 0 00-2 2v4a2 2 0 002 2V6h10a2 2 0 00-2-2H4zm2 6a2 2 0 012-2h8a2 2 0 012 2v4a2 2 0 01-2 2H8a2 2 0 01-2-2v-4zm6 4a2 2 0 100-4 2 2 0 000 4z"
                    clip-rule="evenodd"
                  />
                </svg>
                <span class="flex flex-col text-sm text-gray-500 truncate">
                  <span class="truncate">{{ transaction.accountType }}</span>
                  <span
                    ><span class="font-medium text-gray-900"
                      >${{ transaction.transactionAmount }}</span
                    >
                    RMB</span
                  >
                  <span>{{ transaction.transactionDate }}</span>
                </span>
              </span>
              <!-- Heroicon name: chevron-right -->
              <svg
                class="flex-shrink-0 w-5 h-5 text-gray-400"
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 20 20"
                fill="currentColor"
                aria-hidden="true"
              >
                <path
                  fill-rule="evenodd"
                  d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z"
                  clip-rule="evenodd"
                />
              </svg>
            </span>
          </a>
        </li>

        <!-- More items... -->
      </ul>

      <nav
        class="flex items-center justify-between px-4 py-3 bg-white border-t border-gray-200"
        aria-label="Pagination"
      >
        <div class="flex justify-between flex-1">
          <a
            href="#"
            class="relative inline-flex items-center px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:text-gray-500"
          >
            Previous
          </a>
          <a
            href="#"
            class="relative inline-flex items-center px-4 py-2 ml-3 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:text-gray-500"
          >
            Next
          </a>
        </div>
      </nav>
    </div>

    <!-- Activity table (small breakopoint and up) -->
    <!-- Without this, ONLY smallest viewport displays transaction rows -->
    <div class="hidden sm:block">
      <div class="max-w-6xl px-4 mx-auto sm:px-6 lg:px-8">
        <div class="flex flex-col mt-2">
          <div
            class="min-w-full overflow-hidden overflow-x-auto align-middle shadow sm:rounded-lg"
          >
            <table class="min-w-full divide-y divide-gray-200">
              <!-- Define the static table column headers -->
              <thead>
                <tr>
                  <th
                    class="px-6 py-3 text-xs font-medium tracking-wider text-left text-gray-500 uppercase bg-gray-50"
                  >
                    Transaction
                  </th>
                  <th
                    class="px-6 py-3 text-xs font-medium tracking-wider text-right text-gray-500 uppercase bg-gray-50"
                  >
                    Amount
                  </th>
                  <th
                    class="px-6 py-3 text-xs font-medium tracking-wider text-left text-gray-500 uppercase bg-gray-50 md:block"
                  >
                    Account
                  </th>
                  <th
                    class="px-6 py-3 text-xs font-medium tracking-wider text-left text-gray-500 uppercase bg-gray-50"
                  >
                    Balance
                  </th>
                  <th
                    class="px-6 py-3 text-xs font-medium tracking-wider text-right text-gray-500 uppercase bg-gray-50"
                  >
                    Date
                  </th>
                </tr>
              </thead>
              <!-- Loop over transactions -->
              <tbody
                v-for="transaction in transactions"
                :key="transaction.id"
                class="bg-white divide-y divide-gray-200"
              >
                <tr class="bg-white">
                  <td
                    class="w-full px-6 py-4 text-sm text-gray-900 max-w-0 whitespace-nowrap"
                  >
                    <div class="flex">
                      <a
                        href="#"
                        class="inline-flex text-sm truncate group space-x-2"
                      >
                        <!-- Heroicon name: cash -->
                        <svg
                          class="flex-shrink-0 w-5 h-5 text-gray-400 group-hover:text-gray-500"
                          xmlns="http://www.w3.org/2000/svg"
                          viewBox="0 0 20 20"
                          fill="currentColor"
                          aria-hidden="true"
                        >
                          <path
                            fill-rule="evenodd"
                            d="M4 4a2 2 0 00-2 2v4a2 2 0 002 2V6h10a2 2 0 00-2-2H4zm2 6a2 2 0 012-2h8a2 2 0 012 2v4a2 2 0 01-2 2H8a2 2 0 01-2-2v-4zm6 4a2 2 0 100-4 2 2 0 000 4z"
                            clip-rule="evenodd"
                          />
                        </svg>
                        <p
                          class="text-gray-500 truncate group-hover:text-gray-900"
                        >
                          {{ transaction.notes }}
                        </p>
                      </a>
                    </div>
                  </td>
                  <td
                    class="px-6 py-4 text-sm text-right text-gray-500 whitespace-nowrap"
                  >
                    <span class="font-medium text-gray-900"
                      >¥{{ transaction.transactionAmount }}
                    </span>
                    RMB
                  </td>
                  <td
                    class="hidden px-6 py-4 text-sm text-gray-500 whitespace-nowrap md:block"
                  >
                    <!-- Colored background 'pill'. Could make dynamic based on Account Type -->
                    <span
                      class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-green-100 text-green-800 capitalize"
                    >
                      {{ transaction.accountType }}
                    </span>
                  </td>
                  <td
                    class="px-6 py-4 text-sm text-right text-gray-500 whitespace-nowrap"
                  >
                    ¥{{ transaction.currentBalance }}
                  </td>
                  <td
                    class="px-6 py-4 text-sm text-right text-gray-500 whitespace-nowrap"
                  >
                    {{ transaction.createdAt }}
                  </td>
                </tr>
              </tbody>
            </table>
            <!-- Pagination -->
            <nav
              class="flex items-center justify-between px-4 py-3 bg-white border-t border-gray-200 sm:px-6"
              aria-label="Pagination"
            >
              <div class="hidden sm:block">
                <p class="text-sm text-gray-700">
                  Showing
                  <span class="font-medium">1</span>
                  to
                  <span class="font-medium">10</span>
                  of
                  <!-- Make results a calculated total of transactions -->
                  <span class="font-medium">20</span>
                  results
                </p>
              </div>
              <div class="flex justify-between flex-1 sm:justify-end">
                <a
                  href="#"
                  class="relative inline-flex items-center px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:bg-gray-50"
                >
                  Previous
                </a>
                <a
                  href="#"
                  class="relative inline-flex items-center px-4 py-2 ml-3 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:bg-gray-50"
                >
                  Next
                </a>
              </div>
            </nav>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { db } from "@/firebase/config";
import Navbar from "@/components/Navbar.vue";
import getDocument from "@/composables/getDocument";
import getCollection from "@/composables/getCollection";

export default defineComponent({
  name: "MemberAccountsTransactionsDetails",
  components: { Navbar },
  props: ["id", "type"],
  setup(props) {
    // Let's get our full member document
    const { document: member, error: errorGetDocument } = getDocument(
      "members",
      props.id
    );

    // Let's get our member's transactions collection
    // Q: Use props.id or member.value.id?
    // A: Use props.id! I already have it so don't have to wait for member
    const {
      documents: transactions,
      error: errorGetCollection,
    } = getCollection(`members/${props.id}/transactions`); // Works!
    console.log("transactions", transactions.value);
    console.log("props", props);
    // const {
    //   documents: transactions,
    //   error: errorGetCollection,
    // } = getCollection(`members/${member.value?.id}/transactions`);  // Nope!

    return {
      member,
      transactions,
      errorGetDocument,
      errorGetCollection,
    };
  },
});
</script>

<style>
</style>
