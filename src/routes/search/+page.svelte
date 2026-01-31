<script lang="ts">
    import { onMount } from "svelte";

    let interval = setInterval(() => {
        if (form.search === "") {
            form.search = null
        }
    }, 100)

    

    let array = [
        {path: "/", head: "egg", tail: ""},
        {path: "/", head: "egg", tail: ""},
        {path: "/", head: "egg", tail: ""},
        {path: "/", head: "egg", tail: ""},
        {path: "/", head: "apple", tail: ""},
        {path: "/", head: "arc", tail: ""},
        {path: "/", head: "egg", tail: ""},
        {path: "/", head: "egg", tail: ""},
        {path: "/", head: "egg", tail: ""},


    ]
    

    let form = {
        search:null
    }


   

</script>

<br><br><br>

<h1 class="text-center text-4xl">Search</h1>
<br>

<form class="flex" action="">
    <input  bind:value={form.search} type="text" class="mx-auto border-2 border-black">
</form>
<section class="bg-amber-500 p-4">
    {#each array.filter(e => e.head.toLowerCase().startsWith(form.search!)).slice(0, 4) as item}
        <a href={item.path}>
            <div class="bg-black h-auto w-auto text-white">
                <p>{item.head}</p>
                <p>{item.tail}</p>
                <p>{item.path}</p>
            </div>
        </a>
        <br>

    {/each}
</section>


<br><br><br><br><br><br>
<button class="cursor-pointer" on:click={() => {
    console.log("Form Search", form.search)
}}>Search</button>



