<script>
  let items = [
    { name: 'Manzanas', completed: false },
    { name: 'Bananas', completed: false },
    { name: 'Naranjas', completed: false }
  ];

  let newItem = '';

  function addItem() {
    if (newItem.trim() !== '') {
      items = [...items, { name: newItem, completed: false }];
      newItem = '';
    }
  }

  function removeItem(index) {
    items = items.filter((_, i) => i !== index);
  }

  function toggleComplete(index) {
    items[index].completed = !items[index].completed;
  }
</script>

<h1>Shopping List</h1>

<input type="text" bind:value={newItem} placeholder="Add item">
<button on:click={addItem}>Add</button>

<ul>
  {#each items as item, index}
    <li>
      <span style="text-decoration: {item.completed ? 'line-through' : 'none'}">{item.name}</span>
      <button on:click={() => toggleComplete(index)}>{item.completed ? 'Desmarcar' : 'Completar'}</button>
      <button on:click={() => removeItem(index)}>Remove</button>
    </li>
  {/each}
</ul>

<h1>Completed Items</h1>

<ul>
  {#each items as item, index}
    {#if item.completed}
      <li style="text-decoration: line-through;">{item.name}</li>
    {/if}
  {/each}
</ul>
