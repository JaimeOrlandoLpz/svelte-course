<!--Svelte files are composed of three part-->

<!--Script-->
<script>
    import {v4 as uuid} from "uuid"
    import Counter from "./lib/Counter.svelte";
    import Button from "./lib/Button.svelte";
    import TodoList from "./lib/TodoList.svelte";
    let name = 'Svelte';

    const todos = [
        {
            id: uuid(),
            title: 'Todo 1',
            completed: true
        },
        {
            id: uuid(),
            title: 'Todo 2',
            completed: false
        },
        {
            id: uuid(),
            title: 'Todo 3',
            completed: true
        }
    ]
</script>

<!--Markup-->

<!--Here we use let x to mean that we defined a slot prop x somewhere inside the Button component and we're assigning the value of that prop to a new variable z-->
<!--We can provide event modifiers like 'once' in the example which will make sure that the event only activates 1 time. The list of event modifiers can be consulted in Svelte's documentation-->
<Button
    let:isLeftHovered={isLeftHovered}
    size="large"
    shadow
    disabled
    textColor="blue"
    bgColor="gold"
    on:click|once={()=>{
    alert(true)
    }}

    >
    <span slot="leftContent">Hi Left</span>
    Button Text (slot) Is hovering left: {isLeftHovered}
</Button>

<TodoList todos={todos}></TodoList>



<!--<h1>Hello {name.toLocaleUpperCase()}!</h1>-->
<!--<Counter initialCount={3}/>-->

<!--styles-->
<style>
    h1 {
        color: #646cff;
    }
</style>