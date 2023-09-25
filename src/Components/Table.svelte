<script>
	import { onMount } from "svelte";
	import { setContext } from "svelte";
	import { getContext } from "svelte";
	import { writable } from "svelte/store";
  
	// Create a writable store for drinks
	const drinks = writable([]);
  
	onMount(async () => {
	  fetch("https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Bourbon")
		.then((response) => response.json())
		.then( (data) => {
		  // Assuming data.drinks is an array
		  const drinksData = data.drinks;
		  drinks.set(drinksData); // Set the data in the store
		})
		.catch((error) => {
		  console.log(error);
		});
	});
  
	// console.log('drinks::::', drinks)

	 let table = [{
		"idDrink":"Suraj",
		"strDrink":"publishDate",
		"strDrinkThumb":"modifiedDate"
	 }];

	const watch = drinks.subscribe(async value => {
		console.log('value:::::',value)
		table = value;
  })
	console.log('watch:::::',table)
  </script>
  
  <table class="table table-bordered table-striped">
	<thead>
	  <tr>
		<th>Name</th>
		<th>Publish date</th>
		<th>Modified date</th>
	  </tr>
	</thead>
	<tbody>
		{#each table as row}
		<tr>
		  <td>{row.idDrink}</td>
		  <td>{row.strDrink}</td>
		  <td>{row.strDrinkThumb}</td>
		</tr>
		{/each}
	</tbody>
  </table>