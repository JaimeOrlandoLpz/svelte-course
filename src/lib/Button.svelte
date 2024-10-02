<script>
    export let size = 'small' //Default prop value
    export let shadow = false;
    export let bgColor = undefined;
    export let textColor = undefined;

    let isLeftHovered = false;


    console.log($$slots)

</script>

<!-- In Svelte we use the slot tag to access whatever content was passed between the open and closing tags when calling the component (similar to react children prop)-->
<!--Adding classes dynamically with class directive-->
<!--We can also add styles dynamically through the style directive-->
<!--The on:click without a function means that it will inherit the on click behavior defined in the parent component-->
<button
    on:click
    style:--buttonBgColor={bgColor}
    style:--buttonTextColor={textColor}
    class:size-lg={size === 'large'}
    class:size-sm={size==='small'}
    class:has-left={$$slots.leftContent}
    class:shadow={shadow}
    {...$$restProps}>
    <!--Here we're saying that whichever content we pass from the Parent for the named slot leftContent will be placed here-->
    {#if $$slots.leftContent}
    <div
        class="left-content"
        on:mouseenter={()=>{isLeftHovered=true}}
        on:mouseleave={()=>{isLeftHovered = false}}
    >
        <slot name="leftContent">

        </slot>
    </div>
    {/if}
    <!--Add the slot tag to allow the component to receive child tags-->

    <!--Define a slot prop x-->
    <slot x="y" isLeftHovered={isLeftHovered}>Fallback</slot>
</button>

<style lang="scss">
    button {
        display: flex;
    align-items: center;
        background-color: var(--buttonBgColor);
        color: var(--buttonTextColor);
        border: none;
        padding: 15px;
        font-weight: bold;
        border-radius: 5px;
        cursor: pointer;

        .left-content{
            margin-right: 10px;
        }

        &.size-lg {
            padding: 20px 25px;
        }

        &.size-sm {
            padding: 15px 20px;
        }

        &.shadow{
            box-shadow: 0 0 10px rgba(1,1,1,0.3);
        }

        &:hover {
            background-color: variables.$color;
        }
    }
</style>