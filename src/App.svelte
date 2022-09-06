<script>
  import FeedbackList from "./components/FeedbackList.svelte";
  import FeedbackStats from "./components/FeedbackStats.svelte";
  import FeedbackForm from "./components/FeedbackForm.svelte";

  let feedback = [
    {
      id: 1,
      rating: 10,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
    {
      id: 2,
      rating: 9,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
    {
      id: 3,
      rating: 8,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
  ];

  $: count = feedback.length;
  $: average =
    feedback.reduce((total, { rating }) => total + rating, 0) / count;

  const deleteFeedback = (e) => {
    const itemID = e.detail;
    feedback = feedback.filter((item) => item.id != itemID);
  };
</script>

<main class="container">
  <FeedbackForm />
  <FeedbackStats {count} {average} />
  <FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>
