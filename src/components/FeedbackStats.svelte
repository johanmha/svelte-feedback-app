<script>
  import { FeedbackStore } from '../stores.js';
  $: count = $FeedbackStore.length;
  $: average =
    $FeedbackStore.reduce((total, { rating }) => total + rating, 0) / count;
</script>

<div class="feedback-stats">
  <h4>{count} Reviews</h4>
  <h4>Ratings Average {average}</h4>
</div>

<style>
  .feedback-stats {
    display: flex;
    justify-content: space-between;
    text-align: center;
  }
</style>
