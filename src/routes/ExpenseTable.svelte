<script lang="ts">
  let { rows } = $props()
</script>

<table>
	<thead>
		<tr>
			<th>Date</th>
			<th>Category</th>
			<th>Amount</th>
		</tr>
	</thead>
	<tbody>
		{#each rows as expense (expense.id)}
			<tr>
				<td>{expense.date}</td>
				<td>{expense.category}</td>
				<td>{expense.amount}</td>
			</tr>	
		{/each}
	</tbody>
</table>
{#if rows.length === 0} <p>No expenses.</p> {/if}