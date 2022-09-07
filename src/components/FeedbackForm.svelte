<script>
  import Card from "./Card.svelte";
  import Button from "./Button.svelte";
  let message = "";
  let disabled = true;
  let text = "";
  let min = 10;

  const handleInput = () => {
    if (text.trim().length <= min) {
      disabled = true;
      message = `Text must be at least ${min} characters`;
    } else {
      disabled = false;
      message = "";
    }
  };
</script>

<Card>
  <header>
    <h2>How would you rate you service with us?</h2>
  </header>
  <form>
    <!-- Rating Select -->
    <div class="input-group">
      <input
        type="text"
        placeholder="Tell us your opinion"
        on:input={handleInput}
        bind:value={text}
      />
      <Button {disabled} type="submit">Send</Button>
    </div>
    {#if message}
      <div class="message">{message}</div>
    {/if}
  </form>
</Card>

<style>
  header {
    max-width: 400px;
    margin: auto;
  }
  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }
  .input-group {
    display: flex;
    flex-direction: row;
    padding: 2px;
    border: 1px solid #ccc;
    border-radius: 8px;
    padding: 8px 10px;
    margin-top: 15px;
  }
  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }
  input:focus {
    outline: none;
  }
  .message {
    color: rebeccapurple;
    text-align: center;
    padding-top: 10px;
  }
</style>
