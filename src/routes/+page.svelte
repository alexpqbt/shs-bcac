<script lang="ts">
	import AddExpense from "./AddExpense.svelte";
	import ExpenseTable from "./ExpenseTable.svelte";

	type Expense = {
		id: string,
		date: Date,
		category: string,
		amount: number
	}

	let expenses: Expense[] = $state([])
	let total = $derived(expenses.reduce((acc, curr) => acc + curr.amount, 0))

	function addExpense(value: Expense) {
		expenses.push({ ...value, id: crypto.randomUUID()})
	}
</script>

<AddExpense onsubmit={addExpense}/>
<p>Total Expenses: {total}</p>
<ExpenseTable rows={expenses}/>