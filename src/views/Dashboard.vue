<template>
  <Navbar />
  <div v-if="members">
    <div v-for="member in members" :key="member.id">
      <h2>name: {{ member.name }}</h2>
      <h2>tracker: {{ member.trackerOwner }}</h2>
      <div v-for="account in member.accounts" :key="account.type">
        <h3>type: {{ account.type }}</h3>
        <p>balance: {{ account.balance }}</p>
        <p>
          previousTransactionAmount: {{ account.previousTransactionAmount }}
        </p>
        <p>previousTransactionDate: {{ account.previousTransactionDate }}</p>
      </div>
    </div>
  </div>
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
import getCollection from "@/composables/getCollection";

export default defineComponent({
  name: "Dashboard",
  components: { Navbar },
  setup() {
    const { error, documents: members } = getCollection("members-simple");

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
