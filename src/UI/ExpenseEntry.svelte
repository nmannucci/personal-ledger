<script>
  export let date;
  export let amount;
  export let title;
</script>

<section
  class="mb-6 px-12 py-8 w-3/4 flex justify-around border border-red-400 rounded-lg">
  <div>
    <h1 class="text-3xl font-bold  mb-4">Date</h1>
    <h3 class="text-2xl font-semibold">{date}</h3>
  </div>
  <div>
    <h1 class="text-3xl font-bold  mb-4">Title</h1>
    <h3 class="text-2xl font-semibold">{title}</h3>
  </div>
  <div>
    <h1 class="text-3xl font-bold mb-4">Amount Spent</h1>
    <h3 class="text-2xl font-semibold">$ ({amount * -1})</h3>
  </div>
</section>
