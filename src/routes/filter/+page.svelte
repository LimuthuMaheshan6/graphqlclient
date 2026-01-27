<script lang="ts">
    import axios from "axios";
    import { onMount } from "svelte";

    let observer:IntersectionObserver;
    let url = 'http://localhost:8000/query'

    onMount(() => {
      let trigger = document.querySelector("#trigger")

      observer = new IntersectionObserver((entries) => {
         entries.forEach((entry) => {
            if (entry.isIntersecting && !loadingMore 
                    ) {
                console.log("cursor: ", payload[payload.length - 1]._id)
                loadMore(payload[payload.length - 1]._id)
            }
         })

      })


      observer.observe(trigger!)


    })



    let payload:any[] = [];
    let loading = true;
    let loadingMore = false

    onMount(async () => {
        loadInitial()
    }    
)

        async function loadInitial() {
            

        const query = `
            query {
                users(cursor: "") {
                    _id
                    name
                    email
                }
            }
        `;

        
    
       const response = await axios.post(
            url,
            { query },
            {
                headers: {
                'Content-Type': 'application/json',
                },
            }
            );

            payload = [...payload,...response.data.data.users];
            loading = false
          
            
            console.log("data", response.data.data.users)
            
        

        }


        async function loadMore(Cursor:string) {
            loadingMore = true

            let cur:String = payload[payload.length - 1]._id
     
           

        const query = `
            query {
                users(cursor: "${cur}") {
                    _id
                    name
                    email
                }
            }
        `;

        
    
       const response = await axios.post(
            url,
            { query },
            {
                headers: {
                'Content-Type': 'application/json',
                },
            }
            ).finally(() => {loadingMore = false});

            if (response.data.data.users.length === 0) {
                observer.disconnect()
            }

            payload = [...payload,...response.data.data.users];
            
          
            
            console.log("data", response.data.data.users)
            
        }


</script>



<h1>Hello</h1>
    
<span class="lds-roller"></span>


<!-- first load section --> 
<section>
    
    {#if !loading}
    
        <div  class="flex flex-row justify-items-normal gap-5 flex-wrap">
            {#each payload as item}
            <div class="w-[320px] h-[400px] bg-stone-600 text-white rounded-[12px] mx-auto p-3">
                <p>{item.email}</p>
                <p>{item.name}</p>
               
            
            
            
            
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

                 
                
    </div> 
    
{/if}
 


</section>

<br><br><br>

<div class="w-full h-3 bg-black" id="trigger"></div>


<!-- <div class="w-full h-20 flex justify-center">
<button class="bg-amber-200 text-center h-9 w-15 cursor-pointer" on:click={() => {
    
    loadMore(payload[payload.length - 5].id + 10);
    
}}>CLICK</button>

</div> -->









