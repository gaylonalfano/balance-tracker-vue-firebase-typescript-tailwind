<template>
  <Navbar />
  <!-- <button @click="getTransactions">Get Transactions</button> -->
  <!-- <div v-if="computedTransactionsUsingGetTransactions"> -->
  <!--   <h1>computedTransactionsUsingGetTransactions</h1> -->
  <!--   <div v-for="t in computedTransactionsUsingGetTransactions" :key="t.id"> -->
  <!--     <p>t.id: {{ t.id }}</p> -->
  <!--     <p>t.accountType: {{ t.accountType }}</p> -->
  <!--   </div> -->
  <!-- </div> -->
  <div v-if="transactions">
    <h1>transactions</h1>
    <div v-for="t in transactions" :key="t.id">
      <p>t.id: {{ t.id }} -- type: {{ t.accountType }}</p>
    </div>
  </div>
  <br />
  <br />
  <div v-if="transactionsWithGetCollectionWithQuery">
    <h1>transactionsWithGetCollectionWithQuery</h1>
    <div v-for="t in transactionsWithGetCollectionWithQuery" :key="t.id">
      <p>t.id: {{ t.id }} -- type: {{ t.accountType }}</p>
    </div>
  </div>
  <br />
  <br />
  <div v-if="shaunsTransactions">
    <h1>shaunsTransactions</h1>
    <div v-for="t in shaunsTransactions" :key="t.id">
      <p>t.id: {{ t.id }} -- type: {{ t.accountType }}</p>
    </div>
  </div>
  <br />
  <br />
  <div v-if="transactionsComputed">
    <h1>transactionsComputed</h1>
    <div v-for="t in transactionsComputed" :key="t.id">
      <p>
        t.id: {{ t.id }} -- type: {{ t.accountType }} -- testProp:
        {{ t.testProp }}
      </p>
    </div>
  </div>
  <br />
  <br />
  <div v-if="transactionsWithGetCollectionWithQueryComputed">
    <h1>transactionsWithGetCollectionWithQueryComputed</h1>
    <div
      v-for="t in transactionsWithGetCollectionWithQueryComputed"
      :key="t.id"
    >
      <p>
        t.id: {{ t.id }} -- type: {{ t.accountType }} -- testProp:
        {{ t.testProp }}
      </p>
    </div>
  </div>
  <br />
  <br />
  <div v-if="shaunsTransactionsComputed">
    <h1>shaunsTransactionsComputed</h1>
    <div v-for="t in shaunsTransactionsComputed" :key="t.id">
      <p>
        t.id: {{ t.id }} -- type: {{ t.accountType }} -- testProp:
        {{ t.testProp }}
      </p>
    </div>
  </div>
  <!-- <div v-for="t in getTransactions()" :key="t.id"> -->
  <!--   <p>t.id: {{ t.id }}</p> -->
  <!--   <p>t.accountType: {{ t.accountType }}</p> -->
  <!-- </div> -->
  <!-- <h1>Testing getCollection without the Query param as an option</h1> -->
  <!-- <!-1- <div v-if="transactions"> -1-> -->
  <!-- <!-1-   <div v-for="transaction in transactions" :key="transaction.id"> -1-> -->
  <!-- <!-1-     <p>t.id: {{ transaction.id }}</p> -1-> -->
  <!-- <!-1-     <p>t.accountType: {{ transaction.accountType }}</p> -1-> -->
  <!-- <!-1-   </div> -1-> -->
  <!-- <!-1- </div> -1-> -->
  <!-- <br /> -->
  <!-- <div v-if="computedTransactionsWithComposableApplyingFilter"> -->
  <!--   <div -->
  <!--     v-for="transaction in computedTransactionsWithComposableApplyingFilter" -->
  <!--     :key="transaction.id" -->
  <!--   > -->
  <!--     <p>t.id: {{ transaction.id }}</p> -->
  <!--     <p>t.accountType: {{ transaction.accountType }}</p> -->
  <!--   </div> -->
  <!-- </div> -->
  <!-- <div v-else>NO DATA</div> -->
  <!-- <h1>Testing watchEffect() + route.params + FS Query</h1> -->
  <!-- <div v-if="transactionsQueriedInitial"> -->
  <!--   transactionsQueriedInitial: {{ transactionsQueriedInitial }} -->
  <!-- </div> -->
  <!-- <br /> -->
  <!-- <h3>type: {{ type }}</h3> -->
  <!-- <h3>$route.params.type: {{ $route.params.type }}</h3> -->
  <!-- <h1>Testing computed() route and transactions</h1> -->
  <!-- <div v-if="routeParamsComputed"> -->
  <!--   <h3>$route.params: {{ $route.params }}</h3> -->
  <!--   <h3>routeParamsComputed: {{ routeParamsComputed }}</h3> -->
  <!-- </div> -->
  <!-- <div v-if="filteredTransactions"> -->
  <!--   filteredTransactions: {{ filteredTransactions }} -->
  <!-- </div> -->
  <!-- <div v-if="routeParamsComputedFilteredTransactions"> -->
  <!--   routeParamsComputedFilteredTransactions: -->
  <!--   {{ routeParamsComputedFilteredTransactions }} -->
  <!-- </div> -->
  <!-- <div v-if="computedTransactionsUsingGetCollectionWithRouteParams"> -->
  <!--   computedTransactionsUsingGetCollectionWithRouteParams: -->
  <!--   {{ computedTransactionsUsingGetCollectionWithRouteParams }} -->
  <!-- </div> -->
  <!-- <div v-if="computedTransactionsUsingGetCollectionDestructuredWithRouteParams"> -->
  <!--   computedTransactionsUsingGetCollectionDestructuredWithRouteParams: -->
  <!--   {{ computedTransactionsUsingGetCollectionDestructuredWithRouteParams }} -->
  <!-- </div> -->
  <!-- <div v-if="computedTransactionsWithoutComposable"> -->
  <!--   computedTransactionsWithoutComposable: -->
  <!--   {{ computedTransactionsWithoutComposable }} -->
  <!-- </div> -->
  <!-- <div v-if="computedTransactionsWithoutComposableAwaitPromiseAll"> -->
  <!--   computedTransactionsWithoutComposableAwaitPromiseAll: -->
  <!--   {{ computedTransactionsWithoutComposableAwaitPromiseAll }} -->
  <!-- </div> -->

  <!-- Page header -->
  <!-- <div v-if="member && transactions"> -->
  <!--   <header class="relative z-0 flex-1 overflow-y-auto"> -->
  <!--     <div class="bg-white shadow"> -->
  <!--       <div class="px-4 sm:px-6 lg:max-w-6xl lg:mx-auto lg:px-8"> -->
  <!--         <div -->
  <!--           class="py-6 md:flex md:items-center md:justify-between lg:border-t lg:border-gray-200" -->
  <!--         > -->
  <!--           <div class="flex-1 min-w-0"> -->
  <!--             <!-1- Profile -1-> -->
  <!--             <div class="flex items-center"> -->
  <!--               <img -->
  <!--                 class="hidden w-16 h-16 rounded-full sm:block" -->
  <!--                 src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.6&w=256&h=256&q=80" -->
  <!--                 alt="" -->
  <!--               /> -->
  <!--               <div> -->
  <!--                 <div class="flex items-center"> -->
  <!--                   <h1 -->
  <!--                     class="ml-3 text-2xl font-bold text-gray-900 leading-7 sm:leading-9 sm:truncate" -->
  <!--                   > -->
  <!--                     Good morning, {{ member.name }} -->
  <!--                   </h1> -->
  <!--                 </div> -->
  <!--               </div> -->
  <!--             </div> -->
  <!--           </div> -->
  <!--           <div class="flex mt-6 space-x-3 md:mt-0 md:ml-4"> -->
  <!--             <button -->
  <!--               @click="forceUpdateComponent" -->
  <!--               type="button" -->
  <!--               class="inline-flex items-center px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 shadow-sm rounded-md hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-cyan-500" -->
  <!--             > -->
  <!--               Filter (reload) -->
  <!--             </button> -->
  <!--             <button -->
  <!--               type="button" -->
  <!--               class="inline-flex items-center px-4 py-2 text-sm font-medium text-white bg-indigo-500 border border-transparent shadow-sm rounded-md hover:bg-indigo-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500" -->
  <!--             > -->
  <!--               + Transaction -->
  <!--             </button> -->
  <!--           </div> -->
  <!--         </div> -->
  <!--         <!-1- <!-2- Breadcrumbs -2-> -1-> -->
  <!--         <!-1- <nav class="flex" aria-label="Breadcrumb"> -1-> -->
  <!--         <!-1-   <ol class="flex items-center space-x-4"> -1-> -->
  <!--         <!-1-     <li> -1-> -->
  <!--         <!-1-       <div> -1-> -->
  <!--         <!-1-         <a href="#" class="text-gray-400 hover:text-gray-500"> -1-> -->
  <!--         <!-1-           <!-2- Heroicon name: home -2-> -1-> -->
  <!--         <!-1-           <svg -1-> -->
  <!--         <!-1-             class="flex-shrink-0 w-5 h-5" -1-> -->
  <!--         <!-1-             xmlns="http://www.w3.org/2000/svg" -1-> -->
  <!--         <!-1-             viewBox="0 0 20 20" -1-> -->
  <!--         <!-1-             fill="currentColor" -1-> -->
  <!--         <!-1-             aria-hidden="true" -1-> -->
  <!--         <!-1-           > -1-> -->
  <!--         <!-1-             <path -1-> -->
  <!--         <!-1-               d="M10.707 2.293a1 1 0 00-1.414 0l-7 7a1 1 0 001.414 1.414L4 10.414V17a1 1 0 001 1h2a1 1 0 001-1v-2a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 001 1h2a1 1 0 001-1v-6.586l.293.293a1 1 0 001.414-1.414l-7-7z" -1-> -->
  <!--         <!-1-             /> -1-> -->
  <!--         <!-1-           </svg> -1-> -->
  <!--         <!-1-           <span class="sr-only">Home</span> -1-> -->
  <!--         <!-1-         </a> -1-> -->
  <!--         <!-1-       </div> -1-> -->
  <!--         <!-1-     </li> -1-> -->
  <!--         <!-1-     <li> -1-> -->
  <!--         <!-1-       <div class="flex items-center"> -1-> -->
  <!--         <!-1-         <!-2- Heroicon name: chevron-right -2-> -1-> -->
  <!--         <!-1-         <svg -1-> -->
  <!--         <!-1-           class="flex-shrink-0 w-5 h-5 text-gray-400" -1-> -->
  <!--         <!-1-           xmlns="http://www.w3.org/2000/svg" -1-> -->
  <!--         <!-1-           viewBox="0 0 20 20" -1-> -->
  <!--         <!-1-           fill="currentColor" -1-> -->
  <!--         <!-1-           aria-hidden="true" -1-> -->
  <!--         <!-1-         > -1-> -->
  <!--         <!-1-           <path -1-> -->
  <!--         <!-1-             fill-rule="evenodd" -1-> -->
  <!--         <!-1-             d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" -1-> -->
  <!--         <!-1-             clip-rule="evenodd" -1-> -->
  <!--         <!-1-           /> -1-> -->
  <!--         <!-1-         </svg> -1-> -->
  <!--         <!-1-         <a -1-> -->
  <!--         <!-1-           href="#" -1-> -->
  <!--         <!-1-           class="ml-4 text-sm font-medium text-gray-500 hover:text-gray-700" -1-> -->
  <!--         <!-1-           >Projects</a -1-> -->
  <!--         <!-1-         > -1-> -->
  <!--         <!-1-       </div> -1-> -->
  <!--         <!-1-     </li> -1-> -->
  <!--         <!-1-     <li> -1-> -->
  <!--         <!-1-       <div class="flex items-center"> -1-> -->
  <!--         <!-1-         <!-2- Heroicon name: chevron-right -2-> -1-> -->
  <!--         <!-1-         <svg -1-> -->
  <!--         <!-1-           class="flex-shrink-0 w-5 h-5 text-gray-400" -1-> -->
  <!--         <!-1-           xmlns="http://www.w3.org/2000/svg" -1-> -->
  <!--         <!-1-           viewBox="0 0 20 20" -1-> -->
  <!--         <!-1-           fill="currentColor" -1-> -->
  <!--         <!-1-           aria-hidden="true" -1-> -->
  <!--         <!-1-         > -1-> -->
  <!--         <!-1-           <path -1-> -->
  <!--         <!-1-             fill-rule="evenodd" -1-> -->
  <!--         <!-1-             d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" -1-> -->
  <!--         <!-1-             clip-rule="evenodd" -1-> -->
  <!--         <!-1-           /> -1-> -->
  <!--         <!-1-         </svg> -1-> -->
  <!--         <!-1-         <a -1-> -->
  <!--         <!-1-           href="#" -1-> -->
  <!--         <!-1-           aria-current="page" -1-> -->
  <!--         <!-1-           class="ml-4 text-sm font-medium text-gray-500 hover:text-gray-700" -1-> -->
  <!--         <!-1-           >Project Nero</a -1-> -->
  <!--         <!-1-         > -1-> -->
  <!--         <!-1-       </div> -1-> -->
  <!--         <!-1-     </li> -1-> -->
  <!--         <!-1-   </ol> -1-> -->
  <!--         <!-1- </nav> -1-> -->
  <!--       </div> -->
  <!--     </div> -->
  <!--   </header> -->

  <!--   <!-1- Accounts Cards Overview -1-> -->
  <!--   <main class="pt-8 pb-8 bg-indigo-100"> -->
  <!--     <div class="max-w-6xl px-4 mx-auto sm:px-6 lg:px-8"> -->
  <!--       <h2 class="text-lg font-medium text-gray-900 leading-6">Overview</h2> -->
  <!--       <div> -->
  <!--         <!-1- Simple Account Card -1-> -->
  <!--         <!-1- <dl class="mt-2 grid grid-cols-1 gap-5 sm:grid-cols-3"> -1-> -->
  <!--         <!-1-   <div -1-> -->
  <!--         <!-1-     v-for="account in member.accounts" -1-> -->
  <!--         <!-1-     :key="account.type" -1-> -->
  <!--         <!-1-     class="overflow-hidden bg-white rounded-lg shadow" -1-> -->
  <!--         <!-1-   > -1-> -->
  <!--         <!-1-     <AccountDetailsStatsCard :member="member" /> -1-> -->
  <!--         <!-1-     <!-2- <div class="px-4 py-5 sm:p-6"> -2-> -1-> -->
  <!--         <!-1-     <!-2-   <dt class="text-sm font-medium text-gray-500 truncate"> -2-> -1-> -->
  <!--         <!-1-     <!-2-     {{ account.type }} -2-> -1-> -->
  <!--         <!-1-     <!-2-   </dt> -2-> -1-> -->
  <!--         <!-1-     <!-2-   <dd class="mt-1 text-3xl font-semibold text-gray-900"> -2-> -1-> -->
  <!--         <!-1-     <!-2-     ¥{{ account.currentBalance }} -2-> -1-> -->
  <!--         <!-1-     <!-2-   </dd> -2-> -1-> -->
  <!--         <!-1-     <!-2- </div> -2-> -1-> -->
  <!--         <!-1-   </div> -1-> -->
  <!--         <!-1- </dl> -1-> -->
  <!--         <!-1- Account Stats Card -1-> -->
  <!--         <!-1- UPDATE: After adding :account to AccountDetailsStatsCard, I now need to v-for over the -1-> -->
  <!--         <!-1- member  accounts, otherwise :account="type" isn't enough and account will be undefined -1-> -->
  <!--         <dl class="mt-2 grid grid-cols-1 gap-5 sm:grid-cols-2 lg:grid-cols-3"> -->
  <!--           <div -->
  <!--             v-for="account in member.accounts" -->
  <!--             :key="account" -->
  <!--             class="flex flex-col overflow-hidden bg-white rounded-lg shadow" -->
  <!--           > -->
  <!--             <AccountDetailsStatsCard :member="member" :account="account" /> -->
  <!--           </div> -->
  <!--         </dl> -->
  <!--         <!-1- <AccountDetailsStatsCard :member="member" :account="type" /> -1-> -->
  <!--         <!-1- <!-2- Top part of AccountDetailsStatsCard -2-> -1-> -->
  <!--         <!-1- <dl class="mt-2 grid grid-cols-1 gap-5 sm:grid-cols-2 lg:grid-cols-3"> -1-> -->
  <!--         <!-1-   <div -1-> -->
  <!--         <!-1-     v-for="account in member.accounts" -1-> -->
  <!--         <!-1-     :key="account.type" -1-> -->
  <!--         <!-1-     class="flex flex-col overflow-hidden bg-white rounded-lg shadow" -1-> -->
  <!--         <!-1-   > -1-> -->
  <!--         <!-1-     <div class="flex-grow px-4 py-5 sm:p-6"> -1-> -->
  <!--         <!-1-       <div class="flex items-center"> -1-> -->
  <!--         <!-1-         <div class="flex-1 w-0 ml-5"> -1-> -->
  <!--         <!-1-           <dt class="text-sm font-medium text-gray-500 truncate"> -1-> -->
  <!--         <!-1-             {{ account.type }} -1-> -->
  <!--         <!-1-           </dt> -1-> -->
  <!--         <!-1-           <dd class="flex items-baseline"> -1-> -->
  <!--         <!-1-             <div class="text-2xl font-semibold text-gray-900"> -1-> -->
  <!--         <!-1-               ¥{{ account.currentBalance }} -1-> -->
  <!--         <!-1-             </div> -1-> -->
  <!--         <!-1-             <!-2- Latest Transaction Arrow Indicator -2-> -1-> -->
  <!--         <!-1-             <div -1-> -->
  <!--         <!-1-               v-if="account.latestTransactionAmount > 0" -1-> -->
  <!--         <!-1-               class="flex items-baseline ml-2 text-sm font-semibold text-green-600" -1-> -->
  <!--         <!-1-             > -1-> -->
  <!--         <!-1-               <svg -1-> -->
  <!--         <!-1-                 class="self-center flex-shrink-0 w-5 h-5 text-green-500" -1-> -->
  <!--         <!-1-                 fill="currentColor" -1-> -->
  <!--         <!-1-                 viewBox="0 0 20 20" -1-> -->
  <!--         <!-1-                 aria-hidden="true" -1-> -->
  <!--         <!-1-               > -1-> -->
  <!--         <!-1-                 <path -1-> -->
  <!--         <!-1-                   fill-rule="evenodd" -1-> -->
  <!--         <!-1-                   d="M5.293 9.707a1 1 0 010-1.414l4-4a1 1 0 011.414 0l4 4a1 1 0 01-1.414 1.414L11 7.414V15a1 1 0 11-2 0V7.414L6.707 9.707a1 1 0 01-1.414 0z" -1-> -->
  <!--         <!-1-                   clip-rule="evenodd" -1-> -->
  <!--         <!-1-                 /> -1-> -->
  <!--         <!-1-               </svg> -1-> -->
  <!--         <!-1-               <span class="sr-only"> Increased by </span> -1-> -->
  <!--         <!-1-               {{ account.latestTransactionAmount }} -1-> -->
  <!--         <!-1-             </div> -1-> -->
  <!--         <!-1-             <div -1-> -->
  <!--         <!-1-               v-else -1-> -->
  <!--         <!-1-               class="flex items-baseline ml-2 text-sm font-semibold text-red-600" -1-> -->
  <!--         <!-1-             > -1-> -->
  <!--         <!-1-               <svg -1-> -->
  <!--         <!-1-                 class="self-center flex-shrink-0 w-5 h-5 text-red-500" -1-> -->
  <!--         <!-1-                 fill="currentColor" -1-> -->
  <!--         <!-1-                 viewBox="0 0 20 20" -1-> -->
  <!--         <!-1-                 aria-hidden="true" -1-> -->
  <!--         <!-1-               > -1-> -->
  <!--         <!-1-                 <path -1-> -->
  <!--         <!-1-                   fill-rule="evenodd" -1-> -->
  <!--         <!-1-                   d="M14.707 10.293a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 111.414-1.414L9 12.586V5a1 1 0 012 0v7.586l2.293-2.293a1 1 0 011.414 0z" -1-> -->
  <!--         <!-1-                   clip-rule="evenodd" -1-> -->
  <!--         <!-1-                 /> -1-> -->
  <!--         <!-1-               </svg> -1-> -->
  <!--         <!-1-               <span class="sr-only"> Decreased by </span> -1-> -->
  <!--         <!-1-               {{ account.latestTransactionAmount }} -1-> -->
  <!--         <!-1-             </div> -1-> -->
  <!--         <!-1-           </dd> -1-> -->
  <!--         <!-1-         </div> -1-> -->
  <!--         <!-1-       </div> -1-> -->
  <!--         <!-1-     </div> -1-> -->
  <!--         <!-1-   </div> -1-> -->
  <!--         <!-1- </dl> -1-> -->
  <!--       </div> -->
  <!--     </div> -->

  <!--     <TransactionsDetailsTable :transactions="transactions" /> -->
  <!--     <!-1- UPDATE Trying to replace entire table with TransactionsDetailsTable component -1-> -->
  <!--     <!-1- Wrap entire table with div :key="type" to rerender when type changes -1-> -->
  <!--     <!-1- https://michaelnthiessen.com/key-changing-technique/ -1-> -->
  <!--     <!-1- <div :key="type"> -1-> -->
  <!--     <!-1- <div :key="$route.params.type"> -1-> -->
  <!--     <!-1-   <h2 -1-> -->
  <!--     <!-1-     class="max-w-6xl px-4 mx-auto mt-8 text-lg font-medium text-gray-900 leading-6 sm:px-6 lg:px-8" -1-> -->
  <!--     <!-1-   > -1-> -->
  <!--     <!-1-     Recent activity -1-> -->
  <!--     <!-1-   </h2> -1-> -->
  <!--     <!-1-   <!-2- <button @click="handleFilterByAccount">Filter by Account</button> -2-> -1-> -->

  <!--     <!-1-   <!-2- Activity list (smallest breakopoint only) -2-> -1-> -->
  <!--     <!-1-   <!-2- This WILL display rows even at smallest viewport -2-> -1-> -->
  <!--     <!-1-   <div class="shadow sm:hidden"> -1-> -->
  <!--     <!-1-     <ul -1-> -->
  <!--     <!-1-       v-for="transaction in transactionsQueriedInitial" -1-> -->
  <!--     <!-1-       :key="transaction.id" -1-> -->
  <!--     <!-1-       class="mt-2 overflow-hidden shadow divide-y divide-gray-200 sm:hidden" -1-> -->
  <!--     <!-1-     > -1-> -->
  <!--     <!-1-       <li> -1-> -->
  <!--     <!-1-         <div class="block px-4 py-4 bg-white hover:bg-gray-50"> -1-> -->
  <!--     <!-1-           <span class="flex items-center space-x-4"> -1-> -->
  <!--     <!-1-             <span class="flex flex-1 truncate space-x-2"> -1-> -->
  <!--     <!-1-               <!-2- Heroicon name: cash -2-> -1-> -->
  <!--     <!-1-               <svg -1-> -->
  <!--     <!-1-                 class="flex-shrink-0 w-5 h-5 text-gray-400" -1-> -->
  <!--     <!-1-                 xmlns="http://www.w3.org/2000/svg" -1-> -->
  <!--     <!-1-                 viewBox="0 0 20 20" -1-> -->
  <!--     <!-1-                 fill="currentColor" -1-> -->
  <!--     <!-1-                 aria-hidden="true" -1-> -->
  <!--     <!-1-               > -1-> -->
  <!--     <!-1-                 <path -1-> -->
  <!--     <!-1-                   fill-rule="evenodd" -1-> -->
  <!--     <!-1-                   d="M4 4a2 2 0 00-2 2v4a2 2 0 002 2V6h10a2 2 0 00-2-2H4zm2 6a2 2 0 012-2h8a2 2 0 012 2v4a2 2 0 01-2 2H8a2 2 0 01-2-2v-4zm6 4a2 2 0 100-4 2 2 0 000 4z" -1-> -->
  <!--     <!-1-                   clip-rule="evenodd" -1-> -->
  <!--     <!-1-                 /> -1-> -->
  <!--     <!-1-               </svg> -1-> -->
  <!--     <!-1-               <span class="flex flex-col text-sm text-gray-500 truncate"> -1-> -->
  <!--     <!-1-                 <!-2- <span class="truncate">{{ transaction.accountType }}</span> -2-> -1-> -->
  <!--     <!-1-                 <!-2- Colored background 'pill'. Could make dynamic based on Account Type -2-> -1-> -->
  <!--     <!-1-                 <span -1-> -->
  <!--     <!-1-                   class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-green-100 text-green-800 capitalize" -1-> -->
  <!--     <!-1-                 > -1-> -->
  <!--     <!-1-                   {{ transaction.accountType }} -1-> -->
  <!--     <!-1-                 </span> -1-> -->
  <!--     <!-1-                 <span -1-> -->
  <!--     <!-1-                   ><span class="font-medium text-gray-900" -1-> -->
  <!--     <!-1-                     >${{ transaction.transactionAmount }}</span -1-> -->
  <!--     <!-1-                   > -1-> -->
  <!--     <!-1-                   RMB</span -1-> -->
  <!--     <!-1-                 > -1-> -->
  <!--     <!-1-                 <span>{{ -1-> -->
  <!--     <!-1-                   format(transaction.createdAt.toDate(), "MM/dd/yyyy") -1-> -->
  <!--     <!-1-                 }}</span> -1-> -->
  <!--     <!-1-               </span> -1-> -->
  <!--     <!-1-             </span> -1-> -->
  <!--     <!-1-             <!-2- Heroicon name: chevron-right -2-> -1-> -->
  <!--     <!-1-             <!-2- <svg -2-> -1-> -->
  <!--     <!-1-             <!-2-   class="flex-shrink-0 w-5 h-5 text-gray-400" -2-> -1-> -->
  <!--     <!-1-             <!-2-   xmlns="http://www.w3.org/2000/svg" -2-> -1-> -->
  <!--     <!-1-             <!-2-   viewBox="0 0 20 20" -2-> -1-> -->
  <!--     <!-1-             <!-2-   fill="currentColor" -2-> -1-> -->
  <!--     <!-1-             <!-2-   aria-hidden="true" -2-> -1-> -->
  <!--     <!-1-             <!-2- > -2-> -1-> -->
  <!--     <!-1-             <!-2-   <path -2-> -1-> -->
  <!--     <!-1-             <!-2-     fill-rule="evenodd" -2-> -1-> -->
  <!--     <!-1-             <!-2-     d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" -2-> -1-> -->
  <!--     <!-1-             <!-2-     clip-rule="evenodd" -2-> -1-> -->
  <!--     <!-1-             <!-2-   /> -2-> -1-> -->
  <!--     <!-1-             <!-2- </svg> -2-> -1-> -->
  <!--     <!-1-           </span> -1-> -->
  <!--     <!-1-         </div> -1-> -->
  <!--     <!-1-       </li> -1-> -->

  <!--     <!-1-       <!-2- More items... -2-> -1-> -->
  <!--     <!-1-     </ul> -1-> -->

  <!--     <!-1-     <nav -1-> -->
  <!--     <!-1-       class="flex items-center justify-between px-4 py-3 bg-white border-t border-gray-200" -1-> -->
  <!--     <!-1-       aria-label="Pagination" -1-> -->
  <!--     <!-1-     > -1-> -->
  <!--     <!-1-       <div class="flex justify-between flex-1"> -1-> -->
  <!--     <!-1-         <a -1-> -->
  <!--     <!-1-           href="#" -1-> -->
  <!--     <!-1-           class="relative inline-flex items-center px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:text-gray-500" -1-> -->
  <!--     <!-1-         > -1-> -->
  <!--     <!-1-           Previous -1-> -->
  <!--     <!-1-         </a> -1-> -->
  <!--     <!-1-         <a -1-> -->
  <!--     <!-1-           href="#" -1-> -->
  <!--     <!-1-           class="relative inline-flex items-center px-4 py-2 ml-3 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:text-gray-500" -1-> -->
  <!--     <!-1-         > -1-> -->
  <!--     <!-1-           Next -1-> -->
  <!--     <!-1-         </a> -1-> -->
  <!--     <!-1-       </div> -1-> -->
  <!--     <!-1-     </nav> -1-> -->
  <!--     <!-1-   </div> -1-> -->

  <!--     <!-1-   <!-2- Activity table (small breakopoint and up) -2-> -1-> -->
  <!--     <!-1-   <!-2- Without this, ONLY smallest viewport displays transaction rows -2-> -1-> -->
  <!--     <!-1-   <div class="hidden sm:block"> -1-> -->
  <!--     <!-1-     <div class="max-w-6xl px-4 mx-auto sm:px-6 lg:px-8"> -1-> -->
  <!--     <!-1-       <div class="flex flex-col mt-2"> -1-> -->
  <!--     <!-1-         <div -1-> -->
  <!--     <!-1-           class="min-w-full overflow-hidden overflow-x-auto align-middle shadow sm:rounded-lg" -1-> -->
  <!--     <!-1-         > -1-> -->
  <!--     <!-1-           <table class="min-w-full divide-y divide-gray-200"> -1-> -->
  <!--     <!-1-             <!-2- Define the static table column headers -2-> -1-> -->
  <!--     <!-1-             <thead> -1-> -->
  <!--     <!-1-               <tr> -1-> -->
  <!--     <!-1-                 <th -1-> -->
  <!--     <!-1-                   class="px-6 py-3 text-xs font-medium tracking-wider text-left text-gray-500 uppercase bg-gray-50" -1-> -->
  <!--     <!-1-                 > -1-> -->
  <!--     <!-1-                   Transaction -1-> -->
  <!--     <!-1-                 </th> -1-> -->
  <!--     <!-1-                 <th -1-> -->
  <!--     <!-1-                   class="px-6 py-3 text-xs font-medium tracking-wider text-right text-gray-500 uppercase bg-gray-50" -1-> -->
  <!--     <!-1-                 > -1-> -->
  <!--     <!-1-                   Amount -1-> -->
  <!--     <!-1-                 </th> -1-> -->
  <!--     <!-1-                 <th -1-> -->
  <!--     <!-1-                   class="px-6 py-3 text-xs font-medium tracking-wider text-left text-gray-500 uppercase bg-gray-50 md:block" -1-> -->
  <!--     <!-1-                 > -1-> -->
  <!--     <!-1-                   Account -1-> -->
  <!--     <!-1-                 </th> -1-> -->
  <!--     <!-1-                 <th -1-> -->
  <!--     <!-1-                   class="px-6 py-3 text-xs font-medium tracking-wider text-left text-gray-500 uppercase bg-gray-50" -1-> -->
  <!--     <!-1-                 > -1-> -->
  <!--     <!-1-                   Balance -1-> -->
  <!--     <!-1-                 </th> -1-> -->
  <!--     <!-1-                 <th -1-> -->
  <!--     <!-1-                   class="px-6 py-3 text-xs font-medium tracking-wider text-right text-gray-500 uppercase bg-gray-50" -1-> -->
  <!--     <!-1-                 > -1-> -->
  <!--     <!-1-                   Date -1-> -->
  <!--     <!-1-                 </th> -1-> -->
  <!--     <!-1-               </tr> -1-> -->
  <!--     <!-1-             </thead> -1-> -->
  <!--     <!-1-             <!-2- Loop over transactions -2-> -1-> -->
  <!--     <!-1-             <!-2- Experimenting with filtered transactions (original v-for is transaction in transactions) -2-> -1-> -->
  <!--     <!-1-             <!-2- v-for="transaction in computedTransactionsUsingGetCollectionWithRouteParams" -2-> -1-> -->
  <!--     <!-1-             <tbody -1-> -->
  <!--     <!-1-               v-for="transaction in transactionsQueriedInitial" -1-> -->
  <!--     <!-1-               :key="transaction.id" -1-> -->
  <!--     <!-1-               class="bg-white divide-y divide-gray-200" -1-> -->
  <!--     <!-1-             > -1-> -->
  <!--     <!-1-               <tr class="bg-white"> -1-> -->
  <!--     <!-1-                 <td -1-> -->
  <!--     <!-1-                   class="w-full px-6 py-4 text-sm text-gray-900 max-w-0 whitespace-nowrap" -1-> -->
  <!--     <!-1-                 > -1-> -->
  <!--     <!-1-                   <div class="flex"> -1-> -->
  <!--     <!-1-                     <div -1-> -->
  <!--     <!-1-                       class="inline-flex text-sm truncate group space-x-2" -1-> -->
  <!--     <!-1-                     > -1-> -->
  <!--     <!-1-                       <!-2- Heroicon name: cash -2-> -1-> -->
  <!--     <!-1-                       <svg -1-> -->
  <!--     <!-1-                         class="flex-shrink-0 w-5 h-5 text-gray-400 group-hover:text-gray-500" -1-> -->
  <!--     <!-1-                         xmlns="http://www.w3.org/2000/svg" -1-> -->
  <!--     <!-1-                         viewBox="0 0 20 20" -1-> -->
  <!--     <!-1-                         fill="currentColor" -1-> -->
  <!--     <!-1-                         aria-hidden="true" -1-> -->
  <!--     <!-1-                       > -1-> -->
  <!--     <!-1-                         <path -1-> -->
  <!--     <!-1-                           fill-rule="evenodd" -1-> -->
  <!--     <!-1-                           d="M4 4a2 2 0 00-2 2v4a2 2 0 002 2V6h10a2 2 0 00-2-2H4zm2 6a2 2 0 012-2h8a2 2 0 012 2v4a2 2 0 01-2 2H8a2 2 0 01-2-2v-4zm6 4a2 2 0 100-4 2 2 0 000 4z" -1-> -->
  <!--     <!-1-                           clip-rule="evenodd" -1-> -->
  <!--     <!-1-                         /> -1-> -->
  <!--     <!-1-                       </svg> -1-> -->
  <!--     <!-1-                       <p -1-> -->
  <!--     <!-1-                         class="text-gray-500 truncate group-hover:text-gray-900" -1-> -->
  <!--     <!-1-                       > -1-> -->
  <!--     <!-1-                         {{ transaction.notes }} -1-> -->
  <!--     <!-1-                       </p> -1-> -->
  <!--     <!-1-                     </div> -1-> -->
  <!--     <!-1-                   </div> -1-> -->
  <!--     <!-1-                 </td> -1-> -->
  <!--     <!-1-                 <td -1-> -->
  <!--     <!-1-                   class="px-6 py-4 text-sm text-right text-gray-500 whitespace-nowrap" -1-> -->
  <!--     <!-1-                 > -1-> -->
  <!--     <!-1-                   <span class="font-medium text-gray-900" -1-> -->
  <!--     <!-1-                     >¥{{ transaction.transactionAmount }} -1-> -->
  <!--     <!-1-                   </span> -1-> -->
  <!--     <!-1-                   RMB -1-> -->
  <!--     <!-1-                 </td> -1-> -->
  <!--     <!-1-                 <td -1-> -->
  <!--     <!-1-                   class="px-6 py-4 text-sm text-gray-500 whitespace-nowrap md:block" -1-> -->
  <!--     <!-1-                 > -1-> -->
  <!--     <!-1-                   <!-2- Colored background 'pill'. Could make dynamic based on Account Type -2-> -1-> -->
  <!--     <!-1-                   <span -1-> -->
  <!--     <!-1-                     class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-green-100 text-green-800 capitalize" -1-> -->
  <!--     <!-1-                   > -1-> -->
  <!--     <!-1-                     {{ transaction.accountType }} -1-> -->
  <!--     <!-1-                   </span> -1-> -->
  <!--     <!-1-                 </td> -1-> -->
  <!--     <!-1-                 <td -1-> -->
  <!--     <!-1-                   class="px-6 py-4 text-sm text-right text-gray-500 whitespace-nowrap" -1-> -->
  <!--     <!-1-                 > -1-> -->
  <!--     <!-1-                   <span class="font-medium text-gray-900" -1-> -->
  <!--     <!-1-                     >¥{{ transaction.currentBalance }} -1-> -->
  <!--     <!-1-                   </span> -1-> -->
  <!--     <!-1-                   RMB -1-> -->
  <!--     <!-1-                 </td> -1-> -->
  <!--     <!-1-                 <!-2- <td -2-> -1-> -->
  <!--     <!-1-                 <!-2-   class="px-6 py-4 text-sm text-right text-gray-500 whitespace-nowrap" -2-> -1-> -->
  <!--     <!-1-                 <!-2- > -2-> -1-> -->
  <!--     <!-1-                 <!-2-   ¥{{ transaction.currentBalance }} -2-> -1-> -->
  <!--     <!-1-                 <!-2- </td> -2-> -1-> -->
  <!--     <!-1-                 <td -1-> -->
  <!--     <!-1-                   class="px-6 py-4 text-sm text-right text-gray-500 whitespace-nowrap" -1-> -->
  <!--     <!-1-                 > -1-> -->
  <!--     <!-1-                   {{ -1-> -->
  <!--     <!-1-                     format(transaction.createdAt.toDate(), "MM/dd/yyyy") -1-> -->
  <!--     <!-1-                   }} -1-> -->
  <!--     <!-1-                 </td> -1-> -->
  <!--     <!-1-               </tr> -1-> -->
  <!--     <!-1-             </tbody> -1-> -->
  <!--     <!-1-           </table> -1-> -->
  <!--     <!-1-           <!-2- Pagination -2-> -1-> -->
  <!--     <!-1-           <nav -1-> -->
  <!--     <!-1-             class="flex items-center justify-between px-4 py-3 bg-white border-t border-gray-200 sm:px-6" -1-> -->
  <!--     <!-1-             aria-label="Pagination" -1-> -->
  <!--     <!-1-           > -1-> -->
  <!--     <!-1-             <div class="hidden sm:block"> -1-> -->
  <!--     <!-1-               <p class="text-sm text-gray-700"> -1-> -->
  <!--     <!-1-                 Showing -1-> -->
  <!--     <!-1-                 <span class="font-medium">1</span> -1-> -->
  <!--     <!-1-                 to -1-> -->
  <!--     <!-1-                 <span class="font-medium">10</span> -1-> -->
  <!--     <!-1-                 of -1-> -->
  <!--     <!-1-                 <!-2- Make results a calculated total of transactions -2-> -1-> -->
  <!--     <!-1-                 <span class="font-medium">20</span> -1-> -->
  <!--     <!-1-                 results -1-> -->
  <!--     <!-1-               </p> -1-> -->
  <!--     <!-1-             </div> -1-> -->
  <!--     <!-1-             <div class="flex justify-between flex-1 sm:justify-end"> -1-> -->
  <!--     <!-1-               <a -1-> -->
  <!--     <!-1-                 href="#" -1-> -->
  <!--     <!-1-                 class="relative inline-flex items-center px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:bg-gray-50" -1-> -->
  <!--     <!-1-               > -1-> -->
  <!--     <!-1-                 Previous -1-> -->
  <!--     <!-1-               </a> -1-> -->
  <!--     <!-1-               <a -1-> -->
  <!--     <!-1-                 href="#" -1-> -->
  <!--     <!-1-                 class="relative inline-flex items-center px-4 py-2 ml-3 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:bg-gray-50" -1-> -->
  <!--     <!-1-               > -1-> -->
  <!--     <!-1-                 Next -1-> -->
  <!--     <!-1-               </a> -1-> -->
  <!--     <!-1-             </div> -1-> -->
  <!--     <!-1-           </nav> -1-> -->
  <!--     <!-1-         </div> -1-> -->
  <!--     <!-1-       </div> -1-> -->
  <!--     <!-1-     </div> -1-> -->
  <!--     <!-1-   </div> -1-> -->
  <!--     <!-1- </div> -1-> -->
  <!--   </main> -->
  <!-- </div> -->
  <!-- <div v-else> -->
  <!--   <h3> -->
  <!--     {{ errorGetDocument }} -->
  <!--   </h3> -->
  <!--   <h3> -->
  <!--     <!-1- {{ errorGetCollection }} -1-> -->
  <!--   </h3> -->
  <!-- </div> -->
</template>

<script lang="ts">
import {
  defineComponent,
  computed,
  watchEffect,
  onMounted,
  onUpdated,
  onUnmounted,
} from "vue";
import { useRoute, useRouter } from "vue-router";
import { db } from "@/firebase/config";
import { format } from "date-fns";
import Navbar from "@/components/Navbar.vue";
import AccountDetailsStatsCard from "@/components/AccountDetailsStatsCard.vue";
import TransactionsDetailsTable from "@/components/TransactionsDetailsTable.vue";
import getDocument from "@/composables/getDocument";
import getCollection from "@/composables/getCollection";
import getCollectionWithQuery from "@/composables/getCollectionWithQuery";
import getCollectionShaunJs from "@/composables/getCollectionShaunJs";

export default defineComponent({
  name: "MemberAccountsTransactionsDetails",
  components: { Navbar, AccountDetailsStatsCard, TransactionsDetailsTable },
  props: ["id", "type"],
  setup(props) {
    // Get a router instance to force reload/reroute
    const router = useRouter();

    // Testing out the different Hooks to see when they fire
    onMounted(() => {
      console.log("MOUNTED");
      // getTransactions();  // Seems to work
    });
    onUnmounted(() => console.log("UNMOUNTED"));
    onUpdated(() => {
      console.log("UPDATED");
      // Q: What about router.push with params?
      // A: Nope!
      // router.push({
      //   name: "MemberAccountsTransactionsDetails",
      //   params: { id: props.id, type: props.type },
      // });
      // router.go(0); // Error INFINITE LOOP!
    });

    // Let's get our full member document to pass to embedded AccountDetailsStatsCard
    const { document: member, error: errorGetDocument } = getDocument(
      "members",
      props.id
    );

    // =========== SOLVED! It was TypeScript! ===============
    // =========== UPDATE Troubleshooting filtering Round 3....=============
    // === Comparing different getCollection() versions because I SHOULD be able to use
    // array methods on documents.value...
    const {
      documents: transactions,
      error: errorGetCollection,
    } = getCollection(`members/${props.id}/transactions`); // Works!

    // UPDATE Trying Shaun's JS getCollection.js code to see if any difference
    // in the Types returned, etc. Not sure why I cannot access documents.value.filter
    const {
      documents: shaunsTransactions,
      error: shaunsError,
    } = getCollectionShaunJs(`members/${props.id}/transactions`);

    // UPDATE Going to use my getCollectionWithQuery.ts to compare against without query
    // and Shaun's getCollectionShaunJs
    const {
      documents: transactionsWithGetCollectionWithQuery,
      error: errorGetCollectionWithQuery,
    } = getCollectionWithQuery(`members/${props.id}/transactions`);

    // NOTE My three getCollection() above return the SAME list of transactions. Yay.
    // Now trying to see if they behave the same when using array methods
    const transactionsComputed = computed(() => {
      console.log("transactionsComputed triggered!");
      if (transactions.value) {
        // NOTE Below .map() works!
        // return transactions.value.map((doc) => {
        //   return { ...doc, testProp: "transactionsComputed" };
        // });
        // Let's try .filter() now
        return transactions.value.filter(
          // @ts-ignore
          (doc) => doc.accountType == props.type
        );
      }
    }); // WORKS - Same as others
    const shaunsTransactionsComputed = computed(() => {
      console.log("shaunsTransactionsComputed triggered!");
      if (shaunsTransactions.value) {
        // NOTE Below .map() works!
        // IMPORTANT ONLY Shaun's documents.value complains about Object is possibly 'null'
        // @ts-ignore
        // return shaunsTransactions.value.map((doc) => {
        //   return { ...doc, testProp: "shaunsTransactionsComputed" };
        // });
        // Let's try .filter() now
        return transactions.value.filter(
          // @ts-ignore
          (doc) => doc.accountType == props.type
        );
      }
    }); // WORKS - Same as others (excluding Type complaints)
    const transactionsWithGetCollectionWithQueryComputed = computed(() => {
      console.log("transactionsWithGetCollectionWithQueryComputed triggered!");
      if (transactionsWithGetCollectionWithQuery.value) {
        // NOTE Below .map() works!
        // return transactionsWithGetCollectionWithQuery.value.map((doc) => {
        //   // console.log(doc); // Proxy {previousBalance: 30, memberId: ...}
        //   return {
        //     ...doc,
        //     testProp: "transactionsWithGetCollectionWithQueryComputed",
        //   };
        // });
        // Let's try .filter() now
        return transactionsWithGetCollectionWithQuery.value.filter((doc) => {
          // console.log(doc); // Proxy {previousBalance: 30, memberId: ...}
          // Q: How to access the doc data like we did using .map()?
          // return doc.accountType == "savings"  // Error 'accountType' doesn't exist on type { 'data' ...}
          // return ...doc.accountType == "savings"  // Error cannot find 'doc'
          // return doc["accountType"] == "savings" // Error Element implicitly has type 'any'
          // return doc.data().accountType == "savings"; // Error No TS errors but browser TypeError data isn't function
          // return doc.data()["accountType"] == "savings"; // Error No TS errors but browser TypeError data isn't function
          // return doc.getString("accountType") == "savings" // Vetur 2339 does not exist...
          // return doc.get("accountType") == "savings"; // Error No TS errors but browser TypeError get isn't function
          // let tempDoc = { ...doc };
          // console.log({ tempDoc });  // {tempDoc: {transactionAmount: -10, ...}}
          // console.log(tempDoc); // REAL DATA {transaction: -10, ...}
          // console.log(tempDoc.accountType); // WEIRD! It does log 'spending', 'savings', etc. BUT compile Error TS2339 'accountType' does not exist...
          // console.log(doc.accountType); // WEIRD! It does log 'spending', 'savings', etc. BUT compile Error TS2339 'accountType' does not exist...
          // Q: Is this a TS issue that's preventing this from working???
          // A: OMG! If I ts-ignore it works!!! WTF!? What the hell is wrong with TS2339!?
          // @ts-ignore
          // return doc.accountType == "savings"; // WORKS!
          return doc.accountType == props.type; // WORKS!
        });
      }
    }); // WORKS - Same as others
    // ========= Round 3 (Above) =========

    // Let's get our member's transactions collection
    // ======== Using Composable + FS Query =======
    // Q: How could I filter the table results? Let's try the query param
    // A: WORKS just fine except my table doesn't refresh if I click other cards/routes
    // Q: Use props.id or member.value.id?
    // A: Use props.id! I already have it so don't have to wait for member
    // A: member.value?.id doesn't load as fast or at all if not within v-if
    // const {
    //   documents: transactionsQueriedInitial,
    //   error: errorGetCollectionQueriedInitial,
    // } = getCollection(`members/${props.id}/transactions`, [
    //   "accountType",
    //   "==",
    //   props.type,
    // ]);

    // // Let's get a route object to track
    // // UPDATE: Not needed since I can watch props.type since my cards are wrapped
    // // with the same router-links!
    // const route = useRoute();

    // // Q: What about using watchEffect() instead of computed() to track changs in route.params?
    // // Then go our and refetch the data from FS?
    // watchEffect(() => {
    //   // Q: Will this run when route changes even though it's not a Ref? Is route reactive?
    //   // A: Yes! // Works. Shows my params object e.g, {id: "cfqL....", type: "giving"}
    //   // NOTE This may not be ideal though because it fires EVERY TIME route changes...
    //   // I believe I could add a conditional i.e., if(route.params.type) { watchEffect(() => ...)}
    //   // UPDATE No conditional needed! Just be more granular i.e., route.params.type instead of just route.params
    //   // console.log("watchEffect ran! route.params.type changed!", route.params.type);
    //   // Q: Will it track my props.type change? I don't believe so since they're coming from parent Dashboard...
    //   // A: Yes! Interesting... it's because my cards are wrapped with the same router-links!
    //   console.log("watchEffect ran! props.type changed!", props.type);

    //   // Now let's see if we can refetch data from FS...
    //   // ===== Re-executing getCollection() + FS query =====
    //   // NOTE Seems I MUST have an initial getCollection() OUTSIDE of watchEffect()
    //   // Otherwise it errors saying it can't find transactions even though they're defined here.
    //   // Therefore, I'm making another getCollection() inside but with a new variable name
    //   // e.g., (Initial vs. Updated). This means I need to do some v-if logic with these two
    //   // arrays of documents.
    //   // A: CAN'T DO THIS! These inner scoped vars can't be found and returned by setup()!
    //   // let {
    //   //   documents: transactionsQueriedUpdatedOnWatchEffect,
    //   //   error: errorGetCollectionQueriedUpdatedOnWatchEffect,
    //   // } = await getCollection(`members/${props.id}/transactions`, [
    //   //   "accountType",
    //   //   "==",
    //   //   props.type,
    //   // ]);
    //   // console.log(
    //   //   "transactionsQueriedUpdatedOnWatchEffect.value",
    //   //   transactionsQueriedUpdatedOnWatchEffect.value
    //   // );

    //   // return (
    //   //   await transactionsQueriedUpdatedOnWatchEffect,
    //   //   errorGetCollectionQueriedUpdatedOnWatchEffect
    //   // );

    //   // ===== Force a reload/rerender/refresh of the page =====
    //   // NOTE I noticed that after clicking a new account.type, if I make a code change and save,
    //   // the hot-reloading will refresh the page and my recent activity table updates with the right
    //   // account.type displayed!
    //   // Q: What's the best way to reload/rerender/refresh a page in Vue?
    //   // A: Some ways are better than others. this.$forceUpdate() or :key seems to be preferred
    //   // https://michaelnthiessen.com/force-re-render/
    //   // NOTE I tried the :key="type" approach by wrapping a <div :key="type"> around entire recent
    //   // activity table. No luck.
    //   // NOTE Using this.$forceUpdate() is only available inside methods: Options API
    //   // Let's try using a router instance to reload/reroute
    //   // location.reload() // BAD! Infinite loop terrible approach!
    //   // Q: What about router.push?
    //   // A: Nope!
    //   // router.push({ name: "MemberAccountsTransactionsDetails" }); // Nope
    //   // Q: What about router.push with params?
    //   // A: Nope! Doesn't seem to matter....
    //   // router.push({
    //   //   name: "MemberAccountsTransactionsDetails",
    //   //   params: { id: props.id, type: props.type },
    //   // });
    //   // router.replace({ name: "MemberAccountsTransactionsDetails" }); // Nope
    // });

    // // ======== Using Composable (No FS Query) =======
    // // ==== IMPORTANT: Everything below is troubleshooting. Lots learned but nothing ever worked!
    // // Let's get our member's transactions collection
    // // Q: Use props.id or member.value.id?
    // // A: Use props.id! I already have it so don't have to wait for member
    // // A: member.value?.id doesn't load as fast or at all if not within v-if
    // const {
    //   documents: transactions,
    //   error: errorGetCollection,
    // } = getCollection(`members/${props.id}/transactions`); // Works!
    // console.log("transactions", transactions.value);
    // console.log("props", props);

    // // Q: How could I make my transactions table update based on which account.type is clicked?
    // // Could I get all transactions and somehow use computed() along with route.params?
    // // const route = useRoute();
    // // Q: Do I need to watch() my route? Or will route.params auto update when I click a different card?
    // // A: Don't think it's needed. route.params already captures the changes instantly.
    // // const routeParamsComputed = computed(() => route.params); // ComputedRef<Record<string, string | string[]>>
    // // Q: What about watching the route.params changes and THEN doing the filter? This is what's changing, NOT
    // // my original transactions Ref since I only request ALL transactions ONCE...
    // // const routeParamsComputedFilteredTransactions = computed(
    // //   () => transactions.value?.filter((t) => console.log(t)) // Proxy like below...
    // // );
    // // Q: What about making a new getCollection() request whenever route.params change,
    // // and pass the new route.params.type to the query parameter?
    // // A: Potential? Template displays the {"documents": {"_rawValue": [{"accountType": "spending", ...}]}}
    // // const computedTransactionsUsingGetCollectionWithRouteParams = computed(
    // //   () =>
    // //     getCollection(`members/${props.id}/transactions`, [
    // //       "accountType",
    // //       "==",
    // //       route.params.type,
    // //     ]) // NOTE You can chain documents.value on this but it BLOWS up.
    // // ); // {"documents": {"_rawValue": null, ..., "_value": null}} Doesn't seem to get any data...
    // // console.log(
    // //   "computedTransactionsUsingGetCollectionWithRouteParams.value: ",
    // //   computedTransactionsUsingGetCollectionWithRouteParams.value
    // // ); // {documents: RefImpl, error: RefImpl}
    // // console.log(
    // //   "computedTransactionsUsingGetCollectionWithRouteParams.value.documents: ",
    // //   computedTransactionsUsingGetCollectionWithRouteParams.value.documents
    // // ); // RefImpl {_rawValue: null ..., _value: Proxy}
    // // console.log(
    // //   "computedTransactionsUsingGetCollectionWithRouteParams.value.documents.value: ",
    // //   computedTransactionsUsingGetCollectionWithRouteParams.value.documents
    // //     .value
    // // ); // null

    // // Q: What about making a new getCollection() request whenever route.params change,
    // // and pass the new route.params.type to the query parameter?
    // // NOTE: This is same as above section but this one I'm destructuring my getCollection()
    // // A: Same as above W/O destructuring basically.
    // // const computedTransactionsUsingGetCollectionDestructuredWithRouteParams = computed(
    // //   () => {
    // //     // Let's destructure the composable
    // //     const { documents } = getCollection(
    // //       `members/${props.id}/transactions`,
    // //       ["accountType", "==", route.params.type]
    // //     );
    // //     return documents; // NOTE Same as above W/O destructuring. You can chain documents.value on this but it BLOWS up.
    // //   }
    // // );

    // // UPDATE Going to try to create a function that does the filtering in JS
    // // rather than using the FS query/.where() function. I already have all the transactions
    // // so hoping I can just create a function to perform the filtering. Perhaps pair this
    // // with computed(), watchEffect() and/or onUpdated().
    // // NOTE Shaun did something similar in live-chat using computed() and .map()
    // const computedTransactionsWithComposableApplyingFilter = computed(() => {
    //   if (transactions.value) {
    //     // Now only when we have documents will it fire this internal code
    //     // Want to return a new updated/filtered array based on the account type
    //     transactions.value.filter((transaction) => {
    //       // let transactionsAccountType = transaction['accountType']; // Error
    //       // let transactionsAccountType = transaction.accountType; // Error
    //       // let transactionData = { ...transaction }; // Doesn't error... but it's the big FS object
    //       let transactionData = transaction.data(); // Doesn't error... here, but does in browser: TE: transaction.data is not a function
    //       // return transactionData["accountType"] == "savings";
    //       return transactionData.accountType == "savings";
    //       // return transactionData["accountType"] == props.type;
    //       // return transactionData.accountType == props.type; // Error 'accountType' does not exist
    //     });
    //   }
    // });

    // ========== Not using Composable but FS directly =========
    // Q: What if I don't use getCollection but just db directly?
    // NOTE: I believe there is an issue with using async/await inside higher-order functions (i.e., computed())
    // A: This did not work for me. Issues with pending Promises: https://stackoverflow.com/questions/37576685/using-async-await-with-a-foreach-loop
    // NOTE: Trying this from Shaun: https://youtu.be/vYBc7Le5G6s?t=391
    // Q: What about using await Promise.all(response.docs.filter(async (doc) => ...))
    // const computedTransactionsWithoutComposable = computed(async () => {
    //   // Get a reference to our transactions collection
    //   const transactionsRef = db.collection(`members/${props.id}/transactions`); // CollectionReference<DocumentData>
    //   // Get all the documents in the collection. We don't have access to the data just yet!
    //   const response = await transactionsRef.get(); // QuerySnapshot<DocumentData>
    //   return response.docs.filter((doc) => {
    //     // Get the internal data from each FS doc. We have to use .data() to get the data!
    //     // NOTE We can't just do doc[key]
    //     const transaction = doc.data(); // DocumentData! (e.g., transaction.createdAt, transaction.transactionAmount,etc)
    //     return transaction.accountType == route.params.type;
    //   });
    // });
    // console.log(
    //   "computedTransactionsWithoutComposable.value",
    //   computedTransactionsWithoutComposable.value
    // ); // [object Promise] ComputedRefImpl {_dirty: true, __v_isRef: true, __v_isReadonly: true, _setter: ƒ, effect: ƒ}

    // console.log(
    //   "computedTransactionsWithoutComposable.value.then(r => r)",
    //   computedTransactionsWithoutComposable.value.then((r) => r)
    // ); // [object Promise] ComputedRefImpl {_dirty: true, __v_isRef: true, __v_isReadonly: true, _setter: ƒ, effect: ƒ}

    // Q: What about using await Promise.all(response.docs.filter(async (doc) => ...))
    // const computedTransactionsWithoutComposableAwaitPromiseAll = computed(
    //   async () => {
    //     // Get a reference to our transactions collection
    //     const transactionsRef = db.collection(
    //       `members/${props.id}/transactions`
    //     ); // CollectionReference<DocumentData>
    //     // Get all the documents in the collection. We don't have access to the data just yet!
    //     const response = await transactionsRef.get(); // QuerySnapshot<DocumentData>
    //     await Promise.all(
    //       response.docs.filter(async (doc) => {
    //         // Get the internal data from each FS doc. We have to use .data() to get the data!
    //         // NOTE We can't just do doc[key]
    //         const transaction = await doc.data(); // DocumentData! (e.g., transaction.createdAt, transaction.transactionAmount,etc)
    //         return transaction.accountType == route.params.type;
    //       })
    //     );
    //   }
    // );

    // console.log(
    //   "computedTransactionsWithoutComposableAwaitPromiseAll.value",
    //   computedTransactionsWithoutComposableAwaitPromiseAll.value
    // );

    // IMPORTANT: I can get transactions with a QUERY, OR I get all transactions WITHOUT a query.
    // This would obviously affect the transaction.value value as, without a query, it's a static array of documents
    // Reading: https://blog.logrocket.com/your-guide-to-reactivity-in-vue-js/
    // const filteredTransactions = computed(() => {
    //   // === Using forEach() + temp array
    //   let tempStorage = [];
    //   transactions.value?.forEach((transaction) => {
    //     tempStorage.push(transaction);
    //     // console.log("transaction: ", transaction); // Proxy {createdAt: t, notes: ...}
    //   });
    //   // return tempStorage;

    //   // Using filter()
    //   // return console.log(transactions.value); // Proxy {0: {...}, 1: {...}, etc.} Data is there inside
    //   // Filter our transactions based on route.params (account.type)
    //   // return transactions.value?.filter(
    //   //   // Q: How do I extract the data from the Proxy?
    //   //   // Q: Should I create a temp array to store and push() filtered values?
    //   //   // NOTE I'm testing this out with mario@email.com and Adrian's member doc
    //   //   (transaction) => console.log("transaction: ", transaction) // Proxy {createdAt: t, previousBalance: ....} Data is there inside
    //   //   // (transaction) => console.log("transaction: ", transaction.value) // Error 'value' does not exist
    //   //   // (transaction) => console.log("transaction: ", transaction.value) // Error 'value' does not exist
    //   //   // (transaction) => transaction.data().accountType == route.params.type  // Error no data() on transaction
    //   //   // (transaction) => transaction.accountType == route.params.type // Error accountType does not exist
    //   //   // (transaction) => console.log("transaction.data: ", transaction.data) // undefined x 9
    //   // );
    // });
    // console.log("filteredTransaction", filteredTransactions.value); // undefined initially

    // === UPDATE Trying again just querying FS directly using db.
    async function getTransactions() {
      // const transactionsCollectionRef = db.collection(
      //   `members/${props.id}/transactions`
      // );
      const transactionsQuerySnapshot = await db
        .collection(`members/${props.id}/transactions`)
        .get();
      console.log("transactionsQuerySnapshot: ", transactionsQuerySnapshot);
      const transactions = transactionsQuerySnapshot.docs.map((doc) =>
        doc.data()
      );
      console.log("getTransactions transactions: ", transactions); // WORKS!
      return transactions; // WORKS!
    }

    const computedTransactionsUsingGetTransactions = computed(async () => {
      console.log(
        "computed() triggered! Re-running await getTransactions()..."
      );
      await getTransactions(); // WORKS!
    });

    return {
      member,
      getTransactions,
      computedTransactionsUsingGetTransactions,
      shaunsTransactions,
      shaunsTransactionsComputed,
      transactions,
      transactionsComputed,
      transactionsWithGetCollectionWithQuery,
      transactionsWithGetCollectionWithQueryComputed,
      // computedTransactionsWithComposableApplyingFilter,
      // transactionsQueriedInitial,
      // transactionsQueriedUpdatedOnWatchEffect,
      // filteredTransactions,
      // routeParamsComputed,
      // routeParamsComputedFilteredTransactions,
      // computedTransactionsUsingGetCollectionWithRouteParams,
      // computedTransactionsUsingGetCollectionDestructuredWithRouteParams,
      // computedTransactionsWithoutComposable,
      // computedTransactionsWithoutComposableAwaitPromiseAll,
      // errorGetDocument,
      // errorGetCollection,
      // errorGetCollectionQueriedInitial,
      // errorGetCollectionQueriedUpdatedOnWatchEffect,
      format,
    };
  },
  methods: {
    // Trying to see if I can force reload when route.params.type changes
    // Seems this is only availabe inside Options API methods
    forceUpdateComponent() {
      console.log("forceUpdateComponent CLICKED");
      this.$forceUpdate();
    },
  },
});
</script>

<style>
</style>
