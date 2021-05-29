<script>
    export let polls = [];
    console.log(polls)
</script>
    
<div class="polls">
    <ul>
        {#each polls as poll}
            <li>
                <div>
                    {poll.question}
                </div>
            </li>
        {/each}
    </ul>
</div>


<style>

</style>