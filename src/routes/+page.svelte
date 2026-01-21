<script lang="ts">
    import axios from "axios";
    import { onMount } from "svelte";



    let payload:any[] = [];
    onMount(async () => {


        const query = `
            query {
                posts {
                    id
                    title
                    body
                }
            }
        `;
    
       const response = await axios.post(
            'https://graphqlplaceholder.vercel.app/graphql',
            { query },
            {
                headers: {
                'Content-Type': 'application/json',
                },
            }
            );

            payload = [...payload,...response.data.data.posts];
            
            
            
        }
        
        

    
    
    
)




</script>


<h1>Hello</h1>
<button on:click={() => {
    console.log("Payload",payload)
}}>CLICK</button>

<section class="flex flex-row justify-between gap-5 flex-wrap">
    
    
    {#each payload as item}
    
    
    
        <div class="w-[320px] h-[400px] bg-[grey]">
            <p>{item.id}</p>
            <p>{item.title}</p>
            <p>{item.body}</p>
    
    
    
    
    </div>
    {/each}
    
    
    
</section>
