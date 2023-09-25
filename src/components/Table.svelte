<!-- YourComponent.svelte -->
<script>
	import { fetchData } from '../Api/api';
	import { writable } from 'svelte/store';
	import DataTable, { Head, Body, Row, Cell } from '@smui/data-table';
	import Card, { Content } from '@smui/card';
	const [responseDataStore, errorStore] = [writable(null), writable(null)];
	// const responseDataStore = writable([]);
	// const errorStore = writable(null);

	async function fetchDataAndUpdateStores() {
	  try {
		const data = await fetchData();
		console.log(data)
		// Update the reactive stores
		responseDataStore.set(data.products);
		errorStore.set(null);
	  } catch (err) {
		// Handle errors and update the error store
		responseDataStore.set([]);
		errorStore.set(err.message);
	  }
	}
  
	// Call the fetchDataAndUpdateStores function when the component is initialized
	fetchDataAndUpdateStores();
  </script>
  
  <DataTable stickyHeader table$aria-label="User list" style="width: 100%;">
	<Head>
	  <Row>
		<Cell>Name</Cell>
		<Cell>Username</Cell>
		<Cell>Email</Cell>
	  </Row>
	</Head>
	<Body>
	  {#if $responseDataStore}
		{#each $responseDataStore as item (item.id)}
		  <Row>
			<Cell>{item.title}</Cell>
			<Cell>{item.price}</Cell>
			<Cell>{item.category}</Cell>
		  </Row>
		{/each}
	  {:else if $errorStore}
		<Row>
		  <Cell colspan="3">Error: {$errorStore}</Cell>
		</Row>
	  {/if}
	</Body>
  </DataTable>

  
  