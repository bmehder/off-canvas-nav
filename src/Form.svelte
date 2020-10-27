<script>
  let name, email, phone, message;

  const handleSubmit = () => {
    const submission = { name, email, phone, message };
    console.log(submission);
  };
</script>

<style>
  form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    max-width: 400px;
  }
  input,
  textarea,
  button {
    display: block;
    margin-top: 1em;
    background: #f1f1f1;
    padding: 1em;
    font-size: 16px;
    border: none;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1) inset;
    border-radius: 2px;
  }
  textarea {
    min-height: 150px;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
      Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
  }
  button {
    background: darkorange;
    color: white;
  }
  button:hover {
    transform: scale(0.99);
  }
</style>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="Enter name..." bind:value={name} required />
  <input
    type="email"
    placeholder="Enter email address..."
    bind:value={email}
    required />
  <input
    type="phone"
    placeholder="Enter phone number..."
    bind:value={phone}
    required />
  <textarea
    placeholder="Please type your message..."
    bind:value={message}
    required />
  <button>Send Message</button>
</form>
