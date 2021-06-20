<script>
  import Fa from 'svelte-fa'
  import { faInfoCircle } from '@fortawesome/free-solid-svg-icons'
  import { faTrashAlt } from '@fortawesome/free-solid-svg-icons'

    let newItem = '';

    let todoList = [{text: 'Make to do list', status: true},
                    {text: 'Walk the dog', status: false},
                    {text: 'Do my homework', status: false}];

	function addToList() {
		todoList = [...todoList, {text: newItem, status: false}];
		newItem = '';
	}

	function removeFromList(index) {
		todoList.splice(index, 1)
		todoList = todoList;
    }
</script>

<h1>To-Do List</h1>

<div class="todo">



<br/>
{#each todoList as item, index}
	<input bind:checked={item.status} type="checkbox">
	<span class:checked={item.status}>{item.text}</span>
	<span on:click={() => removeFromList(index)}><Fa icon={faTrashAlt} /></span>
	<br/>
{/each}


<div class="add">
<input bind:value={newItem} type="text" placeholder="new todo item..">
<button on:click={addToList}>Add</button>
</div>

</div>

<div class="info">

<Fa icon={faInfoCircle} /> If you resubmit this page, progress will be lost
</div>


<style>
	.checked {
        text-decoration: line-through;
    }
</style>
