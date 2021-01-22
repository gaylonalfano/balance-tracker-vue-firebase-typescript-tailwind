<template>
  <Navbar />
  <header class="bg-white shadow-sm">
    <div class="max-w-7xl mx-auto py-4 px-4 sm:px-6 lg:px-8">
      <h1 class="text-lg leading-6 font-semibold text-gray-900">Dashboard</h1>
    </div>
  </header>
  <main>
    <div class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
      <!-- Replace with your content -->
      <div v-for="member in members" :key="member.id">
        <MemberAccountsTable :member="member" />
      </div>
      <!-- /End replace -->
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import { db } from "@/firebase/config";
import {
  QueryDocumentSnapshot,
  DocumentData,
  QuerySnapshot,
  Query,
} from "@firebase/firestore-types";
import Navbar from "@/components/Navbar.vue";
import MemberAccountsTable from "@/components/MemberAccountsTable.vue";
import getCollection from "@/composables/getCollection";

export default defineComponent({
  name: "Dashboard",
  components: { Navbar, MemberAccountsTable },
  setup() {
    const { error, documents: members } = getCollection("members");

    return { error, members };
  },

  // ===== OLD Data Model
  // setup() {
  //   // This is a general generic all members collection grab
  //   const { error: membersError, documents: members } = getCollection(
  //     "members"
  //   );

  //   // This grabs a SINGLE member's accounts subcollection and orderBy("createdAt") (by default)
  //   // NOTE This does NOT require a composite index (unlike below)
  //   const {
  //     error: memberTwoAccountsError,
  //     documents: memberTwoAccounts,
  //   } = getCollection("members/S1z2W4pFlzf6CXKwk2Vb/accounts");

  //   // This is a query using where() on a SINGLE member accounts subcollection
  //   // NOTE This requires a COMPOSITE INDEX to be created
  //   const {
  //     error: memberOneAccountsError,
  //     documents: memberOneAccounts,
  //   } = getCollection("members/fwy89arzwfXABvYEbdCo/accounts", [
  //     "type",
  //     "==",
  //     "savings",
  //   ]);

  //   return {
  //     membersError,
  //     members,
  //     memberOneAccountsError,
  //     memberOneAccounts,
  //     memberTwoAccountsError,
  //     memberTwoAccounts,
  //   };
  // },
});
</script>

<style>
</style>
