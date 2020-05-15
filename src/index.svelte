<script>
  const shift = 3;
  let input = "";
  let output = "";

  function encrypt() {
    console.log("Encrypt button was clicked");
    let plainText = input;
    let cipherText = "";

    for (let i = 0; i < plainText.length; i++) {
      //cipherText += plainText.charCodeAt(i) + "|";
      let charCode = plainText.charCodeAt(i);
      charCode += shift;
      cipherText += charCode + "|";
    }

    output = cipherText;
  }

  function decrypt() {
    console.log("Decrypt button was clicked");
    let cipherText = input;
    let plainText = "";
    let charCode = "";

    for (let i = 0; i < cipherText.length; i++) {
      if (cipherText[i] !== "|") {
        charCode += cipherText[i];
      } else {
        charCode -= shift;
        plainText += String.fromCharCode(charCode);
        charCode = "";
      }
    }
    output = plainText;
  }

  function analyse() {
    console.log("Analyse button clicked");
    let cipherText = input;
    let charCode = "";
    let codes = [];
    let analysis = "";

  //create an array of character codes from string
    for (let i = 0; i < cipherText.length; i++) {
      if (cipherText[i] !== "|") {
        charCode += cipherText[i];
      } else {
        codes = [...codes, charCode];
        charCode = "";
      }
    }

  //if the array isnt empty, count all the duplicates
    if (codes.length) {
      codes.sort();
      let currentCode = codes[0];
      let count = 0;

      for (let i = 0; i < codes.length; i++) {
        if (codes[i] === currentCode) {
          count++;
        } else {
          analysis += currentCode + " appears " + count + " times.<br>";
          currentCode = codes[i];
          count = 1;
        }
      }
      analysis += currentCode + " appears " + count + " times.<br>";
    }

    output = analysis;
  }
</script>

<section class="section content">
  <h1>Cipher</h1>

  <label class="label">
    Text:
    <input class="input" type="text" bind:value={input} />
  </label>

  <button class="button is-success" on:click={encrypt}>Encrypt</button>
  <button class="button is-warning" on:click={decrypt}>Decrypt</button>
  <button class="button is-link" on:click={analyse}>Analyse</button>

  <h3>Result:</h3>
  <p>{@html output}</p>

</section>
