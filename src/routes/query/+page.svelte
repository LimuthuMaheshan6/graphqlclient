<script lang="ts">
    import axios from "axios";
    import { onMount } from "svelte";



    let payload:any[] = [];
    let loading = true;
    

    let loadingMore = false

    onMount(async () => {




        const query = `
            query {
                posts(first: 10) {
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
          
            
            
        }
        
        

    
    
    
)



        async function loadMore(Cursor:number) {
            loadingMore = true

            let cursor = Cursor
            
        const query = `
            query {
                posts(first: ${cursor}) {
                    id
                    title
                    body
                }
            }
        `;

        
    
       const response1 = await axios.post(
            'https://graphqlplaceholder.vercel.app/graphql',
            { query },
            {
                headers: {
                'Content-Type': 'application/json',
                },
            }
            ).finally(() => {loadingMore = false})

            payload = [...payload,...response1.data.data.posts];
            

           
            
            
            
        
        }




</script>


<h1>Hello</h1>


<!-- first load section --> 
<section>
    
    {#if !loading}
    
        <div  class="flex flex-row justify-items-normal gap-5 flex-wrap">
            {#each payload as item}
            <div class="w-[320px] h-[400px] bg-stone-600 text-white rounded-[12px] mx-auto p-3">
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
                    <p class="text-[21px] text-center">Camera</p>
                 </div>

                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div>
                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div>
                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div>
                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div><div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div><div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div><div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div>

             

                 
                
            </div>
             




            

    {/if}
    

   
    
    
</section>



             

                 
                
            
<section class="mt-3">


<!--Second Load section-->

{#if loadingMore}
    <div  class="flex flex-row justify-center gap-5 flex-wrap">
                
                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div>

                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div>
                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div>
                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div>
                 <div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div><div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div><div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div><div class="mx-auto w-[320px] h-[400px] bg-gray-200">

                    <div class="mt-3 mx-auto bg-[grey] w-[60%] h-6 animate-pulse"></div>
                    <p class="text-[21px] text-center">Camera</p>
                 </div>

             

                 
                
            </div>
    
{/if}
 


</section>

<br><br>
<div class="w-full h-20 flex justify-center">
<button class="bg-amber-200 text-center h-9 w-15 cursor-pointer" on:click={() => {
    
    loadMore(payload[payload.length - 5].id + 10);
    
}}>CLICK</button>

</div>





