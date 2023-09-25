<!-- YourComponent.svelte -->
<script>
	import { fetchData } from '../Api/api';
	import { writable } from 'svelte/store';
    import LayoutGrid, { Cell } from '@smui/layout-grid';
    import Card, {
    Content,
    PrimaryAction,
    Media,
    MediaContent,
    Actions,
    ActionButtons,
    ActionIcons
  } from '@smui/card';

  import Button, { Label } from '@smui/button';
  import IconButton, { Icon } from '@smui/icon-button';
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


<LayoutGrid>
      {#if $responseDataStore}
          {#each $responseDataStore as item (item.id)}
          <Cell span={3} >
              <Card >
                <PrimaryAction>
                  <Media class="card-media-16x9" aspectRatio="16x9">
                    <img src="{item.thumbnail}" alt="Image Alt Text" width="100%" />
                  </Media>
                  <Content class="mdc-typography--body2">
                    <h2 class="mdc-typography--headline6" style="margin: 0;">
                      {item.title}
                    </h2>
                    <h3
                      class="mdc-typography--subtitle2"
                      style="margin: 0 0 10px; color: #888;"
                    >
                      And a subtitle.
                    </h3>
                    {item.description}
                  </Content>
                </PrimaryAction>
                <Actions>
                  <ActionButtons>
                    <Button>
                      <Label>Action</Label>
                    </Button>
                    <Button>
                      <Label>Another</Label>
                    </Button>
                  </ActionButtons>
                  <!-- <ActionIcons>
                    <IconButton
                      toggle
                      aria-label="Add to favorites"
                      title="Add to favorites"
                    >
                      <Icon class="material-icons" on>favorite</Icon>
                      <Icon class="material-icons">favorite_border</Icon>
                    </IconButton>
                    <IconButton class="material-icons" title="Share">
                      share
                    </IconButton>
                    <IconButton class="material-icons" title="More options">
                      more_vert
                    </IconButton>
                  </ActionIcons> -->
                </Actions>
              </Card>
            </Cell>
          {/each}
    
      {:else if $errorStore}
        <Card padded>{$errorStore}</Card>
      {/if}
</LayoutGrid>