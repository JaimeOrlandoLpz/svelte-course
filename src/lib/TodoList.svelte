<script>
    import { createEventDispatcher } from "svelte";
    import Button from "./Button.svelte";
    export let todos = [];
    let input;
    let inputOption2 = "";

    const dispatch = createEventDispatcher();
    const handleAddToDo = () => {
        dispatch('addtodo', {
            title: input.value
        });

        input.value = "";
    };
</script>

<div class="todo-list-wrapper">
    <!-- Iterating over a collection to render HTML elements -->
    <!-- The (todo.id) is used to give each element of the each loop a unique id, which is useful for multiple functionalities -->
    <ul>
        {#each todos as todo, index (todo.id)}
            {@const number = index + 1}
            <li>{number}: {todo.title}</li>
        {/each}
    </ul>

    <form class="add-todo-form" on:submit|preventDefault={handleAddToDo}>
        <!-- bind binds the html element of the input to a desired variable  -->
        <input bind:this={input} />
        <!-- We can use the on:input event to execute a function when an input changes (as an alternative) -->
        <!-- <input on:input={(e)=>{
            inputOption2 = e.currentTarget.value;
        }}/> -->

        <!-- The preferred svelte way is to directly bind the value of the input to a variable -->
        <input bind:value={inputOption2} />
        <p>Input Option 2 value: {inputOption2}</p>
        <Button type="submit" bgColor="crimson" disabled={!input}>Add</Button>
    </form>
</div>
