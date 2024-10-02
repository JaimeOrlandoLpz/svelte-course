<script>
    export let initialCount; // Define as prop (will come from the outside)
    let count = initialCount;
    let string = `Times clicked: ${count}`

    // This is a Svelte reactive statement. This block will execute every time the states referenced inside change value (count in this case) 
    $:{
        string = `Times clicked: ${count}`
    }
</script>

<button on:click={()=>{
    count++;
}}>{string} Counter in State {count}</button>

<style>
    button {
        padding: 15px;
    }
</style>