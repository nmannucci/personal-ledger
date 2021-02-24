<script>
  import { createEventDispatcher } from "svelte";
  import Button from "./UI/Button.svelte";

  let amount = null;
  let date = "";
  let savingsPerc = 0;
  let title = "";

  let dispatch = createEventDispatcher();

  function submitForm() {
    dispatch("save", {
      date: date,
      amount: amount,
      savingsPerc: savingsPerc,
      title: title,
    });

    dispatch("total", {
      amount: amount,
      savingsPerc: savingsPerc,
    });

    date = "";
    amount = "";
    savingsPerc = 0;
    title = "";
  }
</script>

<section class="flex justify-center mb-20 ">
  <form
    on:submit|preventDefault={submitForm}
    class="w-3/4 flex justify-around items-end relative ">
    <div>
      <label for="date" class="text-xl mt-10 mb-2">Date</label>
      <input
        value={date}
        on:input={(event) => (date = event.target.value)}
        placeholder={'1/1/2020'}
        type="text"
        class="bg-transparent border-b border-gray-200 border-t-0 border-l-0 border-r-0 outline-none text-xl focus:border-pink-400" />
    </div>

    <div>
      <label for="date" class="text-xl mt-10 mb-2">Title</label>
      <input
        value={title}
        on:input={(event) => (title = event.target.value)}
        placeholder={'Clothes'}
        type="text"
        class="bg-transparent border-b border-gray-200 border-t-0 border-l-0 border-r-0 outline-none text-xl focus:border-pink-400" />
    </div>

    <div>
      <label for="amount" class="text-xl mt-10 mb-2 ">Amount</label>
      <input
        placeholder="100"
        value={amount}
        on:input={(event) => (amount = event.target.value)}
        type="text"
        class="bg-transparent border-b border-gray-200 border-t-0 border-l-0 border-r-0 outline-none text-xl focus:border-pink-400" />
    </div>

    <div>
      <label for="savingsPerc" class="text-xl mt-10 mb-2 ">Savings %</label>
      <input
        value={savingsPerc}
        on:input={(event) => (savingsPerc = event.target.value)}
        placeholder="0.4"
        type="text"
        class="bg-transparent border-b border-gray-200 border-t-0 border-l-0 border-r-0 outline-none text-xl focus:border-pink-400" />
    </div>
    <Button on:click={submitForm} />
  </form>
</section>
