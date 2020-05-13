<script>
  const shift = 3
  let input = "";
  let output = "";

  function encrypt() {
    console.log("Encrypt button was clicked");
    let plainText = input;
    let cipherText = "";

    for (let i = 0; i < plainText.length; i++) {
      //cipherText += plainText.charCodeAt(i) + "|";
      let charCode = plainText.charCodeAt(i)
      charCode += shift
      cipherText += charCode + '|'
    }

    output = cipherText;
  }

  function decrypt(){
    console.log("Decrypt button was clicked");
    let cipherText = input
    let plainText = ''
    let charCode = ''

    for(let i = 0; i < cipherText.length; i++){
      if(cipherText[i] !== '|'){
        charCode += cipherText[i]
      } else{
        charCode -= shift
        plainText += String.fromCharCode(charCode)
        charCode = ''
      }
    }
    output = plainText
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

  <h3>Result:</h3>

  <p>{output}</p>
</section>
