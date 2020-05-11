<script>
  let input = "";
  let output = "";

  function encrypt() {
    console.log("Encrypt button clicked");
    let plainText = input;
    let cipherText = "";

    for (let i = 0; i < plainText.length; i++) {
      cipherText += plainText.charCodeAt(i) + "|";
    }

    output = cipherText;
  }
</script>

<section class="section content">
  <h1>Cipher</h1>

  <label>
    Text:
    <input type="text" bind:value={input} />
  </label>

  <button on:click={encrypt}>Encrypt</button>

  <h2>Result:</h2>

  <p>{output}</p>
</section>
