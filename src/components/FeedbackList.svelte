<script>
  import FeedbackItem from "./FeedbackItem.svelte";
  export let feedback = [];
</script>

<div>
  {#each feedback as fb}
    <FeedbackItem item={fb} on:delete-feedback />
  {/each}
</div>
