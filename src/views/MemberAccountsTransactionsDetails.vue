<template>
  <Navbar />
  <!-- <h1>Testing watchEffect() + route.params + FS Query</h1> -->
  <!-- <div v-if="transactionsQueriedInitial"> -->
  <!--   transactionsQueriedInitial: {{ transactionsQueriedInitial }} -->
  <!-- </div> -->
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
  <div v-if="member && transactionsQueriedInitial">
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
                @click="forceUpdateComponent"
                type="button"
                class="inline-flex items-center px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 shadow-sm rounded-md hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-cyan-500"
              >
                Filter (reload)
              </button>
              <button
                type="button"
                class="inline-flex items-center px-4 py-2 text-sm font-medium text-white bg-indigo-500 border border-transparent shadow-sm rounded-md hover:bg-indigo-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
              >
                + Transaction
              </button>
            </div>
          </div>
          <!-- <!-1- Breadcrumbs -1-> -->
          <!-- <nav class="flex" aria-label="Breadcrumb"> -->
          <!--   <ol class="flex items-center space-x-4"> -->
          <!--     <li> -->
          <!--       <div> -->
          <!--         <a href="#" class="text-gray-400 hover:text-gray-500"> -->
          <!--           <!-1- Heroicon name: home -1-> -->
          <!--           <svg -->
          <!--             class="flex-shrink-0 w-5 h-5" -->
          <!--             xmlns="http://www.w3.org/2000/svg" -->
          <!--             viewBox="0 0 20 20" -->
          <!--             fill="currentColor" -->
          <!--             aria-hidden="true" -->
          <!--           > -->
          <!--             <path -->
          <!--               d="M10.707 2.293a1 1 0 00-1.414 0l-7 7a1 1 0 001.414 1.414L4 10.414V17a1 1 0 001 1h2a1 1 0 001-1v-2a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 001 1h2a1 1 0 001-1v-6.586l.293.293a1 1 0 001.414-1.414l-7-7z" -->
          <!--             /> -->
          <!--           </svg> -->
          <!--           <span class="sr-only">Home</span> -->
          <!--         </a> -->
          <!--       </div> -->
          <!--     </li> -->
          <!--     <li> -->
          <!--       <div class="flex items-center"> -->
          <!--         <!-1- Heroicon name: chevron-right -1-> -->
          <!--         <svg -->
          <!--           class="flex-shrink-0 w-5 h-5 text-gray-400" -->
          <!--           xmlns="http://www.w3.org/2000/svg" -->
          <!--           viewBox="0 0 20 20" -->
          <!--           fill="currentColor" -->
          <!--           aria-hidden="true" -->
          <!--         > -->
          <!--           <path -->
          <!--             fill-rule="evenodd" -->
          <!--             d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" -->
          <!--             clip-rule="evenodd" -->
          <!--           /> -->
          <!--         </svg> -->
          <!--         <a -->
          <!--           href="#" -->
          <!--           class="ml-4 text-sm font-medium text-gray-500 hover:text-gray-700" -->
          <!--           >Projects</a -->
          <!--         > -->
          <!--       </div> -->
          <!--     </li> -->
          <!--     <li> -->
          <!--       <div class="flex items-center"> -->
          <!--         <!-1- Heroicon name: chevron-right -1-> -->
          <!--         <svg -->
          <!--           class="flex-shrink-0 w-5 h-5 text-gray-400" -->
          <!--           xmlns="http://www.w3.org/2000/svg" -->
          <!--           viewBox="0 0 20 20" -->
          <!--           fill="currentColor" -->
          <!--           aria-hidden="true" -->
          <!--         > -->
          <!--           <path -->
          <!--             fill-rule="evenodd" -->
          <!--             d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" -->
          <!--             clip-rule="evenodd" -->
          <!--           /> -->
          <!--         </svg> -->
          <!--         <a -->
          <!--           href="#" -->
          <!--           aria-current="page" -->
          <!--           class="ml-4 text-sm font-medium text-gray-500 hover:text-gray-700" -->
          <!--           >Project Nero</a -->
          <!--         > -->
          <!--       </div> -->
          <!--     </li> -->
          <!--   </ol> -->
          <!-- </nav> -->
        </div>
      </div>
    </header>

    <!-- Accounts Cards Overview -->
    <main class="pt-8 pb-8 bg-indigo-100">
      <div class="max-w-6xl px-4 mx-auto sm:px-6 lg:px-8">
        <h2 class="text-lg font-medium text-gray-900 leading-6">Overview</h2>
        <div>
          <!-- Simple Account Card -->
          <!-- <dl class="mt-2 grid grid-cols-1 gap-5 sm:grid-cols-3"> -->
          <!--   <div -->
          <!--     v-for="account in member.accounts" -->
          <!--     :key="account.type" -->
          <!--     class="overflow-hidden bg-white rounded-lg shadow" -->
          <!--   > -->
          <!--     <AccountDetailsStatsCard :member="member" /> -->
          <!--     <!-1- <div class="px-4 py-5 sm:p-6"> -1-> -->
          <!--     <!-1-   <dt class="text-sm font-medium text-gray-500 truncate"> -1-> -->
          <!--     <!-1-     {{ account.type }} -1-> -->
          <!--     <!-1-   </dt> -1-> -->
          <!--     <!-1-   <dd class="mt-1 text-3xl font-semibold text-gray-900"> -1-> -->
          <!--     <!-1-     ¥{{ account.currentBalance }} -1-> -->
          <!--     <!-1-   </dd> -1-> -->
          <!--     <!-1- </div> -1-> -->
          <!--   </div> -->
          <!-- </dl> -->
          <!-- Account Stats Card -->
          <!-- UPDATE: After adding :account to AccountDetailsStatsCard, I now need to v-for over the -->
          <!-- member  accounts, otherwise :account="type" isn't enough and account will be undefined -->
          <dl class="mt-2 grid grid-cols-1 gap-5 sm:grid-cols-2 lg:grid-cols-3">
            <div
              v-for="account in member.accounts"
              :key="account"
              class="flex flex-col overflow-hidden bg-white rounded-lg shadow"
            >
              <AccountDetailsStatsCard :member="member" :account="account" />
            </div>
          </dl>
          <!-- <AccountDetailsStatsCard :member="member" :account="type" /> -->
          <!-- <!-1- Top part of AccountDetailsStatsCard -1-> -->
          <!-- <dl class="mt-2 grid grid-cols-1 gap-5 sm:grid-cols-2 lg:grid-cols-3"> -->
          <!--   <div -->
          <!--     v-for="account in member.accounts" -->
          <!--     :key="account.type" -->
          <!--     class="flex flex-col overflow-hidden bg-white rounded-lg shadow" -->
          <!--   > -->
          <!--     <div class="flex-grow px-4 py-5 sm:p-6"> -->
          <!--       <div class="flex items-center"> -->
          <!--         <div class="flex-1 w-0 ml-5"> -->
          <!--           <dt class="text-sm font-medium text-gray-500 truncate"> -->
          <!--             {{ account.type }} -->
          <!--           </dt> -->
          <!--           <dd class="flex items-baseline"> -->
          <!--             <div class="text-2xl font-semibold text-gray-900"> -->
          <!--               ¥{{ account.currentBalance }} -->
          <!--             </div> -->
          <!--             <!-1- Latest Transaction Arrow Indicator -1-> -->
          <!--             <div -->
          <!--               v-if="account.latestTransactionAmount > 0" -->
          <!--               class="flex items-baseline ml-2 text-sm font-semibold text-green-600" -->
          <!--             > -->
          <!--               <svg -->
          <!--                 class="self-center flex-shrink-0 w-5 h-5 text-green-500" -->
          <!--                 fill="currentColor" -->
          <!--                 viewBox="0 0 20 20" -->
          <!--                 aria-hidden="true" -->
          <!--               > -->
          <!--                 <path -->
          <!--                   fill-rule="evenodd" -->
          <!--                   d="M5.293 9.707a1 1 0 010-1.414l4-4a1 1 0 011.414 0l4 4a1 1 0 01-1.414 1.414L11 7.414V15a1 1 0 11-2 0V7.414L6.707 9.707a1 1 0 01-1.414 0z" -->
          <!--                   clip-rule="evenodd" -->
          <!--                 /> -->
          <!--               </svg> -->
          <!--               <span class="sr-only"> Increased by </span> -->
          <!--               {{ account.latestTransactionAmount }} -->
          <!--             </div> -->
          <!--             <div -->
          <!--               v-else -->
          <!--               class="flex items-baseline ml-2 text-sm font-semibold text-red-600" -->
          <!--             > -->
          <!--               <svg -->
          <!--                 class="self-center flex-shrink-0 w-5 h-5 text-red-500" -->
          <!--                 fill="currentColor" -->
          <!--                 viewBox="0 0 20 20" -->
          <!--                 aria-hidden="true" -->
          <!--               > -->
          <!--                 <path -->
          <!--                   fill-rule="evenodd" -->
          <!--                   d="M14.707 10.293a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 111.414-1.414L9 12.586V5a1 1 0 012 0v7.586l2.293-2.293a1 1 0 011.414 0z" -->
          <!--                   clip-rule="evenodd" -->
          <!--                 /> -->
          <!--               </svg> -->
          <!--               <span class="sr-only"> Decreased by </span> -->
          <!--               {{ account.latestTransactionAmount }} -->
          <!--             </div> -->
          <!--           </dd> -->
          <!--         </div> -->
          <!--       </div> -->
          <!--     </div> -->
          <!--   </div> -->
          <!-- </dl> -->
        </div>
      </div>

      <TransactionsDetailsTable :transactions="transactionsQueriedInitial" />
      <!-- UPDATE Trying to replace entire table with TransactionsDetailsTable component -->
      <!-- Wrap entire table with div :key="type" to rerender when type changes -->
      <!-- https://michaelnthiessen.com/key-changing-technique/ -->
      <!-- <div :key="type"> -->
      <!-- <div :key="$route.params.type"> -->
      <!--   <h2 -->
      <!--     class="max-w-6xl px-4 mx-auto mt-8 text-lg font-medium text-gray-900 leading-6 sm:px-6 lg:px-8" -->
      <!--   > -->
      <!--     Recent activity -->
      <!--   </h2> -->
      <!--   <!-1- <button @click="handleFilterByAccount">Filter by Account</button> -1-> -->

      <!--   <!-1- Activity list (smallest breakopoint only) -1-> -->
      <!--   <!-1- This WILL display rows even at smallest viewport -1-> -->
      <!--   <div class="shadow sm:hidden"> -->
      <!--     <ul -->
      <!--       v-for="transaction in transactionsQueriedInitial" -->
      <!--       :key="transaction.id" -->
      <!--       class="mt-2 overflow-hidden shadow divide-y divide-gray-200 sm:hidden" -->
      <!--     > -->
      <!--       <li> -->
      <!--         <div class="block px-4 py-4 bg-white hover:bg-gray-50"> -->
      <!--           <span class="flex items-center space-x-4"> -->
      <!--             <span class="flex flex-1 truncate space-x-2"> -->
      <!--               <!-1- Heroicon name: cash -1-> -->
      <!--               <svg -->
      <!--                 class="flex-shrink-0 w-5 h-5 text-gray-400" -->
      <!--                 xmlns="http://www.w3.org/2000/svg" -->
      <!--                 viewBox="0 0 20 20" -->
      <!--                 fill="currentColor" -->
      <!--                 aria-hidden="true" -->
      <!--               > -->
      <!--                 <path -->
      <!--                   fill-rule="evenodd" -->
      <!--                   d="M4 4a2 2 0 00-2 2v4a2 2 0 002 2V6h10a2 2 0 00-2-2H4zm2 6a2 2 0 012-2h8a2 2 0 012 2v4a2 2 0 01-2 2H8a2 2 0 01-2-2v-4zm6 4a2 2 0 100-4 2 2 0 000 4z" -->
      <!--                   clip-rule="evenodd" -->
      <!--                 /> -->
      <!--               </svg> -->
      <!--               <span class="flex flex-col text-sm text-gray-500 truncate"> -->
      <!--                 <!-1- <span class="truncate">{{ transaction.accountType }}</span> -1-> -->
      <!--                 <!-1- Colored background 'pill'. Could make dynamic based on Account Type -1-> -->
      <!--                 <span -->
      <!--                   class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-green-100 text-green-800 capitalize" -->
      <!--                 > -->
      <!--                   {{ transaction.accountType }} -->
      <!--                 </span> -->
      <!--                 <span -->
      <!--                   ><span class="font-medium text-gray-900" -->
      <!--                     >${{ transaction.transactionAmount }}</span -->
      <!--                   > -->
      <!--                   RMB</span -->
      <!--                 > -->
      <!--                 <span>{{ -->
      <!--                   format(transaction.createdAt.toDate(), "MM/dd/yyyy") -->
      <!--                 }}</span> -->
      <!--               </span> -->
      <!--             </span> -->
      <!--             <!-1- Heroicon name: chevron-right -1-> -->
      <!--             <!-1- <svg -1-> -->
      <!--             <!-1-   class="flex-shrink-0 w-5 h-5 text-gray-400" -1-> -->
      <!--             <!-1-   xmlns="http://www.w3.org/2000/svg" -1-> -->
      <!--             <!-1-   viewBox="0 0 20 20" -1-> -->
      <!--             <!-1-   fill="currentColor" -1-> -->
      <!--             <!-1-   aria-hidden="true" -1-> -->
      <!--             <!-1- > -1-> -->
      <!--             <!-1-   <path -1-> -->
      <!--             <!-1-     fill-rule="evenodd" -1-> -->
      <!--             <!-1-     d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" -1-> -->
      <!--             <!-1-     clip-rule="evenodd" -1-> -->
      <!--             <!-1-   /> -1-> -->
      <!--             <!-1- </svg> -1-> -->
      <!--           </span> -->
      <!--         </div> -->
      <!--       </li> -->

      <!--       <!-1- More items... -1-> -->
      <!--     </ul> -->

      <!--     <nav -->
      <!--       class="flex items-center justify-between px-4 py-3 bg-white border-t border-gray-200" -->
      <!--       aria-label="Pagination" -->
      <!--     > -->
      <!--       <div class="flex justify-between flex-1"> -->
      <!--         <a -->
      <!--           href="#" -->
      <!--           class="relative inline-flex items-center px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:text-gray-500" -->
      <!--         > -->
      <!--           Previous -->
      <!--         </a> -->
      <!--         <a -->
      <!--           href="#" -->
      <!--           class="relative inline-flex items-center px-4 py-2 ml-3 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:text-gray-500" -->
      <!--         > -->
      <!--           Next -->
      <!--         </a> -->
      <!--       </div> -->
      <!--     </nav> -->
      <!--   </div> -->

      <!--   <!-1- Activity table (small breakopoint and up) -1-> -->
      <!--   <!-1- Without this, ONLY smallest viewport displays transaction rows -1-> -->
      <!--   <div class="hidden sm:block"> -->
      <!--     <div class="max-w-6xl px-4 mx-auto sm:px-6 lg:px-8"> -->
      <!--       <div class="flex flex-col mt-2"> -->
      <!--         <div -->
      <!--           class="min-w-full overflow-hidden overflow-x-auto align-middle shadow sm:rounded-lg" -->
      <!--         > -->
      <!--           <table class="min-w-full divide-y divide-gray-200"> -->
      <!--             <!-1- Define the static table column headers -1-> -->
      <!--             <thead> -->
      <!--               <tr> -->
      <!--                 <th -->
      <!--                   class="px-6 py-3 text-xs font-medium tracking-wider text-left text-gray-500 uppercase bg-gray-50" -->
      <!--                 > -->
      <!--                   Transaction -->
      <!--                 </th> -->
      <!--                 <th -->
      <!--                   class="px-6 py-3 text-xs font-medium tracking-wider text-right text-gray-500 uppercase bg-gray-50" -->
      <!--                 > -->
      <!--                   Amount -->
      <!--                 </th> -->
      <!--                 <th -->
      <!--                   class="px-6 py-3 text-xs font-medium tracking-wider text-left text-gray-500 uppercase bg-gray-50 md:block" -->
      <!--                 > -->
      <!--                   Account -->
      <!--                 </th> -->
      <!--                 <th -->
      <!--                   class="px-6 py-3 text-xs font-medium tracking-wider text-left text-gray-500 uppercase bg-gray-50" -->
      <!--                 > -->
      <!--                   Balance -->
      <!--                 </th> -->
      <!--                 <th -->
      <!--                   class="px-6 py-3 text-xs font-medium tracking-wider text-right text-gray-500 uppercase bg-gray-50" -->
      <!--                 > -->
      <!--                   Date -->
      <!--                 </th> -->
      <!--               </tr> -->
      <!--             </thead> -->
      <!--             <!-1- Loop over transactions -1-> -->
      <!--             <!-1- Experimenting with filtered transactions (original v-for is transaction in transactions) -1-> -->
      <!--             <!-1- v-for="transaction in computedTransactionsUsingGetCollectionWithRouteParams" -1-> -->
      <!--             <tbody -->
      <!--               v-for="transaction in transactionsQueriedInitial" -->
      <!--               :key="transaction.id" -->
      <!--               class="bg-white divide-y divide-gray-200" -->
      <!--             > -->
      <!--               <tr class="bg-white"> -->
      <!--                 <td -->
      <!--                   class="w-full px-6 py-4 text-sm text-gray-900 max-w-0 whitespace-nowrap" -->
      <!--                 > -->
      <!--                   <div class="flex"> -->
      <!--                     <div -->
      <!--                       class="inline-flex text-sm truncate group space-x-2" -->
      <!--                     > -->
      <!--                       <!-1- Heroicon name: cash -1-> -->
      <!--                       <svg -->
      <!--                         class="flex-shrink-0 w-5 h-5 text-gray-400 group-hover:text-gray-500" -->
      <!--                         xmlns="http://www.w3.org/2000/svg" -->
      <!--                         viewBox="0 0 20 20" -->
      <!--                         fill="currentColor" -->
      <!--                         aria-hidden="true" -->
      <!--                       > -->
      <!--                         <path -->
      <!--                           fill-rule="evenodd" -->
      <!--                           d="M4 4a2 2 0 00-2 2v4a2 2 0 002 2V6h10a2 2 0 00-2-2H4zm2 6a2 2 0 012-2h8a2 2 0 012 2v4a2 2 0 01-2 2H8a2 2 0 01-2-2v-4zm6 4a2 2 0 100-4 2 2 0 000 4z" -->
      <!--                           clip-rule="evenodd" -->
      <!--                         /> -->
      <!--                       </svg> -->
      <!--                       <p -->
      <!--                         class="text-gray-500 truncate group-hover:text-gray-900" -->
      <!--                       > -->
      <!--                         {{ transaction.notes }} -->
      <!--                       </p> -->
      <!--                     </div> -->
      <!--                   </div> -->
      <!--                 </td> -->
      <!--                 <td -->
      <!--                   class="px-6 py-4 text-sm text-right text-gray-500 whitespace-nowrap" -->
      <!--                 > -->
      <!--                   <span class="font-medium text-gray-900" -->
      <!--                     >¥{{ transaction.transactionAmount }} -->
      <!--                   </span> -->
      <!--                   RMB -->
      <!--                 </td> -->
      <!--                 <td -->
      <!--                   class="px-6 py-4 text-sm text-gray-500 whitespace-nowrap md:block" -->
      <!--                 > -->
      <!--                   <!-1- Colored background 'pill'. Could make dynamic based on Account Type -1-> -->
      <!--                   <span -->
      <!--                     class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-green-100 text-green-800 capitalize" -->
      <!--                   > -->
      <!--                     {{ transaction.accountType }} -->
      <!--                   </span> -->
      <!--                 </td> -->
      <!--                 <td -->
      <!--                   class="px-6 py-4 text-sm text-right text-gray-500 whitespace-nowrap" -->
      <!--                 > -->
      <!--                   <span class="font-medium text-gray-900" -->
      <!--                     >¥{{ transaction.currentBalance }} -->
      <!--                   </span> -->
      <!--                   RMB -->
      <!--                 </td> -->
      <!--                 <!-1- <td -1-> -->
      <!--                 <!-1-   class="px-6 py-4 text-sm text-right text-gray-500 whitespace-nowrap" -1-> -->
      <!--                 <!-1- > -1-> -->
      <!--                 <!-1-   ¥{{ transaction.currentBalance }} -1-> -->
      <!--                 <!-1- </td> -1-> -->
      <!--                 <td -->
      <!--                   class="px-6 py-4 text-sm text-right text-gray-500 whitespace-nowrap" -->
      <!--                 > -->
      <!--                   {{ -->
      <!--                     format(transaction.createdAt.toDate(), "MM/dd/yyyy") -->
      <!--                   }} -->
      <!--                 </td> -->
      <!--               </tr> -->
      <!--             </tbody> -->
      <!--           </table> -->
      <!--           <!-1- Pagination -1-> -->
      <!--           <nav -->
      <!--             class="flex items-center justify-between px-4 py-3 bg-white border-t border-gray-200 sm:px-6" -->
      <!--             aria-label="Pagination" -->
      <!--           > -->
      <!--             <div class="hidden sm:block"> -->
      <!--               <p class="text-sm text-gray-700"> -->
      <!--                 Showing -->
      <!--                 <span class="font-medium">1</span> -->
      <!--                 to -->
      <!--                 <span class="font-medium">10</span> -->
      <!--                 of -->
      <!--                 <!-1- Make results a calculated total of transactions -1-> -->
      <!--                 <span class="font-medium">20</span> -->
      <!--                 results -->
      <!--               </p> -->
      <!--             </div> -->
      <!--             <div class="flex justify-between flex-1 sm:justify-end"> -->
      <!--               <a -->
      <!--                 href="#" -->
      <!--                 class="relative inline-flex items-center px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:bg-gray-50" -->
      <!--               > -->
      <!--                 Previous -->
      <!--               </a> -->
      <!--               <a -->
      <!--                 href="#" -->
      <!--                 class="relative inline-flex items-center px-4 py-2 ml-3 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:bg-gray-50" -->
      <!--               > -->
      <!--                 Next -->
      <!--               </a> -->
      <!--             </div> -->
      <!--           </nav> -->
      <!--         </div> -->
      <!--       </div> -->
      <!--     </div> -->
      <!--   </div> -->
      <!-- </div> -->
    </main>
  </div>
  <div v-else>
    <h3>
      {{ errorGetDocument }}
    </h3>
    <h3>
      <!-- {{ errorGetCollection }} -->
    </h3>
  </div>
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

export default defineComponent({
  name: "MemberAccountsTransactionsDetails",
  components: { Navbar, AccountDetailsStatsCard, TransactionsDetailsTable },
  props: ["id", "type"],
  setup(props) {
    // Get a router instance to force reload/reroute
    const router = useRouter();

    // Testing out the different Hooks to see when they fire
    onMounted(() => console.log("MOUNTED"));
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

    // Let's get our member's transactions collection
    // ======== Using Composable + FS Query =======
    // Q: How could I filter the table results? Let's try the query param
    // A: WORKS just fine except my table doesn't refresh if I click other cards/routes
    // Q: Use props.id or member.value.id?
    // A: Use props.id! I already have it so don't have to wait for member
    // A: member.value?.id doesn't load as fast or at all if not within v-if
    const {
      documents: transactionsQueriedInitial,
      error: errorGetCollectionQueriedInitial,
    } = getCollection(`members/${props.id}/transactions`, [
      "accountType",
      "==",
      props.type,
    ]);

    // Let's get a route object to track
    // UPDATE: Not needed since I can watch props.type since my cards are wrapped
    // with the same router-links!
    const route = useRoute();

    // Q: What about using watchEffect() instead of computed() to track changs in route.params?
    // Then go our and refetch the data from FS?
    watchEffect(() => {
      // Q: Will this run when route changes even though it's not a Ref? Is route reactive?
      // A: Yes! // Works. Shows my params object e.g, {id: "cfqL....", type: "giving"}
      // NOTE This may not be ideal though because it fires EVERY TIME route changes...
      // I believe I could add a conditional i.e., if(route.params.type) { watchEffect(() => ...)}
      // UPDATE No conditional needed! Just be more granular i.e., route.params.type instead of just route.params
      // console.log("watchEffect ran! route.params.type changed!", route.params.type);
      // Q: Will it track my props.type change? I don't believe so since they're coming from parent Dashboard...
      // A: Yes! Interesting... it's because my cards are wrapped with the same router-links!
      console.log("watchEffect ran! props.type changed!", props.type);

      // Now let's see if we can refetch data from FS...
      // ===== Re-executing getCollection() + FS query =====
      // NOTE Seems I MUST have an initial getCollection() OUTSIDE of watchEffect()
      // Otherwise it errors saying it can't find transactions even though they're defined here.
      // Therefore, I'm making another getCollection() inside but with a new variable name
      // e.g., (Initial vs. Updated). This means I need to do some v-if logic with these two
      // arrays of documents.
      // A: CAN'T DO THIS! These inner scoped vars can't be found and returned by setup()!
      // let {
      //   documents: transactionsQueriedUpdatedOnWatchEffect,
      //   error: errorGetCollectionQueriedUpdatedOnWatchEffect,
      // } = await getCollection(`members/${props.id}/transactions`, [
      //   "accountType",
      //   "==",
      //   props.type,
      // ]);
      // console.log(
      //   "transactionsQueriedUpdatedOnWatchEffect.value",
      //   transactionsQueriedUpdatedOnWatchEffect.value
      // );

      // return (
      //   await transactionsQueriedUpdatedOnWatchEffect,
      //   errorGetCollectionQueriedUpdatedOnWatchEffect
      // );

      // ===== Force a reload/rerender/refresh of the page =====
      // NOTE I noticed that after clicking a new account.type, if I make a code change and save,
      // the hot-reloading will refresh the page and my recent activity table updates with the right
      // account.type displayed!
      // Q: What's the best way to reload/rerender/refresh a page in Vue?
      // A: Some ways are better than others. this.$forceUpdate() or :key seems to be preferred
      // https://michaelnthiessen.com/force-re-render/
      // NOTE I tried the :key="type" approach by wrapping a <div :key="type"> around entire recent
      // activity table. No luck.
      // NOTE Using this.$forceUpdate() is only available inside methods: Options API
      // Let's try using a router instance to reload/reroute
      // location.reload() // BAD! Infinite loop terrible approach!
      // Q: What about router.push?
      // A: Nope!
      // router.push({ name: "MemberAccountsTransactionsDetails" }); // Nope
      // Q: What about router.push with params?
      // A: Nope! Doesn't seem to matter....
      // router.push({
      //   name: "MemberAccountsTransactionsDetails",
      //   params: { id: props.id, type: props.type },
      // });
      // router.replace({ name: "MemberAccountsTransactionsDetails" }); // Nope
    });

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
    // // console.log("transactions", transactions.value);
    // // console.log("props", props);

    // // Q: How could I make my transactions table update based on which account.type is clicked?
    // // Could I get all transactions and somehow use computed() along with route.params?
    // const route = useRoute();
    // // Q: Do I need to watch() my route? Or will route.params auto update when I click a different card?
    // // A: Don't think it's needed. route.params already captures the changes instantly.
    // const routeParamsComputed = computed(() => route.params); // ComputedRef<Record<string, string | string[]>>
    // // Q: What about watching the route.params changes and THEN doing the filter? This is what's changing, NOT
    // // my original transactions Ref since I only request ALL transactions ONCE...
    // const routeParamsComputedFilteredTransactions = computed(
    //   () => transactions.value?.filter((t) => console.log(t)) // Proxy like below...
    // );
    // // Q: What about making a new getCollection() request whenever route.params change,
    // // and pass the new route.params.type to the query parameter?
    // // A: Potential? Template displays the {"documents": {"_rawValue": [{"accountType": "spending", ...}]}}
    // const computedTransactionsUsingGetCollectionWithRouteParams = computed(
    //   () =>
    //     getCollection(`members/${props.id}/transactions`, [
    //       "accountType",
    //       "==",
    //       route.params.type,
    //     ]) // NOTE You can chain documents.value on this but it BLOWS up.
    // ); // {"documents": {"_rawValue": null, ..., "_value": null}} Doesn't seem to get any data...
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
    // const computedTransactionsUsingGetCollectionDestructuredWithRouteParams = computed(
    //   () => {
    //     // Let's destructure the composable
    //     const { documents } = getCollection(
    //       `members/${props.id}/transactions`,
    //       ["accountType", "==", route.params.type]
    //     );
    //     return documents; // NOTE Same as above W/O destructuring. You can chain documents.value on this but it BLOWS up.
    //   }
    // );

    // // ========== Not using Composable but FS directly =========
    // // Q: What if I don't use getCollection but just db directly?
    // // NOTE: I believe there is an issue with using async/await inside higher-order functions (i.e., computed())
    // // A: This did not work for me. Issues with pending Promises: https://stackoverflow.com/questions/37576685/using-async-await-with-a-foreach-loop
    // // NOTE: Trying this from Shaun: https://youtu.be/vYBc7Le5G6s?t=391
    // // Q: What about using await Promise.all(response.docs.filter(async (doc) => ...))
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
    // // console.log(
    // //   "computedTransactionsWithoutComposable.value",
    // //   computedTransactionsWithoutComposable.value
    // // ); // [object Promise] ComputedRefImpl {_dirty: true, __v_isRef: true, __v_isReadonly: true, _setter: ƒ, effect: ƒ}

    // // console.log(
    // //   "computedTransactionsWithoutComposable.value.then(r => r)",
    // //   computedTransactionsWithoutComposable.value.then((r) => r)
    // // ); // [object Promise] ComputedRefImpl {_dirty: true, __v_isRef: true, __v_isReadonly: true, _setter: ƒ, effect: ƒ}

    // // Q: What about using await Promise.all(response.docs.filter(async (doc) => ...))
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

    // // console.log(
    // //   "computedTransactionsWithoutComposableAwaitPromiseAll.value",
    // //   computedTransactionsWithoutComposableAwaitPromiseAll.value
    // // );

    // // IMPORTANT: I can get transactions with a QUERY, OR I get all transactions WITHOUT a query.
    // // This would obviously affect the transaction.value value as, without a query, it's a static array of documents
    // // Reading: https://blog.logrocket.com/your-guide-to-reactivity-in-vue-js/
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

    return {
      member,
      // transactions,
      transactionsQueriedInitial,
      // transactionsQueriedUpdatedOnWatchEffect,
      // filteredTransactions,
      // routeParamsComputed,
      // routeParamsComputedFilteredTransactions,
      // computedTransactionsUsingGetCollectionWithRouteParams,
      // computedTransactionsUsingGetCollectionDestructuredWithRouteParams,
      // computedTransactionsWithoutComposable,
      // computedTransactionsWithoutComposableAwaitPromiseAll,
      errorGetDocument,
      // errorGetCollection,
      errorGetCollectionQueriedInitial,
      // errorGetCollectionQueriedUpdatedOnWatchEffect,
      format,
    };
  },
  methods: {
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
