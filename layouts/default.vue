<template>
  <v-app>
    <v-main>
      <h1>AES256 Example</h1>
      <v-container>
        <h3>Encryption</h3>
        <v-text-field
          v-model="plainText"
          label="plaintext"
          @keyup="encrypt"
        ></v-text-field>
        <p>Cipher Text: {{ cipherText }}</p>
      </v-container>
      <v-container>
        <h3>Decryption</h3>
        <v-text-field
          v-model="cipherTextInput"
          label="cipertext"
          @keyup="decrypt"
        ></v-text-field>
        <p>Plaintext Text: {{ plainTextOutput }}</p>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
const CryptoJS = require('crypto-js')

export default {
  data() {
    return {
      plainText: '',
      cipherText: '',
      cipherTextInput: '',
      plainTextOutput: '',
    }
  },
  methods: {
    encrypt() {
      this.cipherText = CryptoJS.AES.encrypt(
        this.plainText,
        'secret key 123'
      ).toString()
    },
    decrypt() {
      const bytes = CryptoJS.AES.decrypt(this.cipherTextInput, 'secret key 123')
      this.plainTextOutput = bytes.toString(CryptoJS.enc.Utf8)
    },
  },
}
</script>
