<script>
  //TODO: Add title to entry
  export let date;
  export let amount;
  export let savingsPerc;
  export let title;

  $: savings = parseFloat((amount * savingsPerc).toFixed(2));
  $: available = parseFloat((amount - savings).toFixed(2));
</script>

<section
  class=" mb-6 px-12 py-8 w-3/4 flex justify-between border border-green-400 rounded-lg">
  <div>
    <h1 class="text-3xl font-bold  mb-4">Date</h1>
    <h3 class="text-2xl font-semibold">{date}</h3>
  </div>
  <div>
    <h1 class="text-3xl font-bold  mb-4">Title</h1>
    <h3 class="text-2xl font-semibold">{title}</h3>
  </div>
  <div>
    <h1 class="text-3xl font-bold mb-4">Gross Amount</h1>
    <h3 class="text-2xl font-semibold">$ {amount}</h3>
  </div>
  <div>
    <h1 class="text-3xl font-bold mb-4">Amount Available</h1>
    <h3 class="text-2xl font-semibold">$ {available}</h3>
  </div>
  <div>
    <h1 class="text-3xl font-bold mb-4">Savings</h1>
    <h3 class="text-2xl font-semibold">$ {savings}</h3>
  </div>
</section>
