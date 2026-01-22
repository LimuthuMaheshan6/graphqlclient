<script lang="ts">
    import axios from "axios";
    import { onMount } from "svelte";



    let payload:any[] = [];
    let loading = true;

    let loadingMore = false
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
            loading = false
            loadingMore = false
            
            
            
        }
        
        

    
    
    
)




</script>


<h1>Hello</h1>
<button on:click={() => {
    console.log("Payload",payload)
}}>CLICK</button>

<section>
    
    {#if !loading}
    
        <div  class="flex flex-row justify-items-normal gap-5 flex-wrap">
            {#each payload as item}
            <div class="w-[320px] h-[400px] bg-[grey] mx-auto">
                <p>{item.id}</p>
                <p>{item.title}</p>
                <p>{item.body}</p>
            
            
            
            
                </div>
            
            
            
            
            
            
                {/each}
        </div>
    {:else}
            <div  class="flex flex-row justify-center gap-5 flex-wrap">
                
                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                 </div>

                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                 </div>
                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                 </div>
                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                 </div>

                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                 </div><div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                 </div><div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                 </div>

                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                 </div><div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                 </div><div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                 </div><div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                 </div>
                 

                 
                
            </div>
             




            

    {/if}
    

    {#if loadingMore}
            <div>Loading More...</div>
    {/if}
    
    
</section>
