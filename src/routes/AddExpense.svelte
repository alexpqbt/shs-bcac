<script lang="ts">
  let { onsubmit } = $props()

  const today = () => new Date().toLocaleDateString("en-CA")
  let date = $state(today())
  let category = $state('')
  let amount = $state(0)

  function handleSubmit(e: Event) {
    e.preventDefault()
    onsubmit({ date, category, amount })
    date = today()
    category = ''
    amount = 0
  }
</script>

<form onsubmit={handleSubmit}>
  <input type="date" name="date" id="date" bind:value={date} required>
  <input type="text" name="category" id="category" bind:value={category} required>
  <input type="number" name="amount" id="amount" min="0" step="any" bind:value={amount} required>
  <button type="submit">Submit</button>
</form>