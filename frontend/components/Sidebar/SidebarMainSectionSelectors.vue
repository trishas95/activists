<template>
  <div class="flex flex-col justify-center mx-2 transition-all duration-500">
    <div class="p-1 space-y-1 rounded-md bg-light-header dark:bg-dark-header">
      <MenuSelector
        :selected="false"
        iconURL="bi:calendar-check"
        btnText="Events"
        btnURL="/"
      ></MenuSelector>
      <MenuSelector
        :selected="false"
        iconURL="bi:person-square"
        btnText="Organizations"
        btnURL="/"
      ></MenuSelector>
    </div>
  </div>
</template>
