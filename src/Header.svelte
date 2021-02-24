<script>
  export let name;
  export let totalEarned;
  export let totalSavings;
  export let totalAvailable;
</script>

<header class="flex items-center justify-between mb-5">
  <h1
    class="text-5xl font-bold leading-tight bg-gradient-to-r from-green-400 to-blue-500 bg-clip-text text-transparent">
    Welcome
    {name},
    <br />
    This is your Personal Ledger
  </h1>
  <div class="mr-14">
    <h3 class="mb-3 text-2xl font-semibold">Total earned: ${totalEarned}</h3>
    <h3 class="mb-3 text-2xl font-semibold">
      Total available: ${totalAvailable}
    </h3>
    <h3 class="text-2xl font-semibold">Total savings: ${totalSavings}</h3>
  </div>
</header>
