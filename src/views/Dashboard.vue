<template>
  <Navbar />
  <div v-if="memberOneAccounts">
    <h1>memberOneAccounts:</h1>
    {{ memberOneAccounts }}
  </div>
  <div v-if="memberTwoAccounts">
    <h1>memberTwoAccounts:</h1>
    {{ memberTwoAccounts }}
  </div>
  <div v-if="membersError">members error: {{ membersError }}</div>
  <div v-if="memberOneAccountsError">
    memberOneAccountsError: {{ memberOneAccountsError }}
  </div>
  <div v-if="memberTwoAccountsError">
    memberTwoAccountsError: {{ memberTwoAccountsError }}
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
    // This is a general generic all members collection grab
    const { error: membersError, documents: members } = getCollection(
      "members"
    );

    // This grabs a SINGLE member's accounts subcollection and orderBy("createdAt") (by default)
    // NOTE This does NOT require a composite index (unlike below)
    const {
      error: memberTwoAccountsError,
      documents: memberTwoAccounts,
    } = getCollection("members/S1z2W4pFlzf6CXKwk2Vb/accounts");

    // This is a query using where() on a SINGLE member accounts subcollection
    // NOTE This requires a COMPOSITE INDEX to be created
    const {
      error: memberOneAccountsError,
      documents: memberOneAccounts,
    } = getCollection("members/fwy89arzwfXABvYEbdCo/accounts", [
      "type",
      "==",
      "savings",
    ]);

    return {
      membersError,
      members,
      memberOneAccountsError,
      memberOneAccounts,
      memberTwoAccountsError,
      memberTwoAccounts,
    };
  },
});
</script>

<style>
</style>
