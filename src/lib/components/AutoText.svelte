<script>
  import { onMount } from 'svelte';

  export let sentences = ['a spiderman walking']; // Default sentence
  let currentText = '';
  let index = 0; // Index of the current sentence in the array
  let charIndex = 0; // Index of the current character in the sentence

  const typingSpeed = 100; // Speed of typing in milliseconds
  const pauseBetweenSentences = 2000; // Pause between sentences in milliseconds

  const typeText = () => {
    if (charIndex < sentences[index].length) {
      currentText += sentences[index].charAt(charIndex);
      charIndex++;
      setTimeout(typeText, typingSpeed);
    } else {
      setTimeout(nextSentence, pauseBetweenSentences);
    }
  };

  const nextSentence = () => {
    index = (index + 1) % sentences.length; // Move to the next sentence, loop back to the first
    currentText = ''; // Clear the current text
    charIndex = 0; // Reset character index
    typeText(); // Start typing the next sentence
  };

  onMount(() => {
    typeText(); // Start typing when the component is mounted
  });

  // Function to calculate the width based on the sentence length
  const calculateWidth = (sentence) => {
    const baseWidth = 1; // Minimum width
    const charWidth = 0.6; // Estimated width per character (em units)
    return `${baseWidth + charWidth * sentence.length}em`;
  };
</script>

<div>
  <input type="text" value={currentText} readonly style="width: {calculateWidth(sentences[index])};" />
</div>

<style>
  input {
    font-size: 1.2em;
    border: 2px solid #333;
    padding: 0.5em;
    color: rgba(255, 255, 255, 0.5);
    position: absolute;
    bottom: 10%;
    left: 50%;
    transform: translateX(-50%);
    border-radius: 5px;
    background-color: rgba(13, 19, 32, 0.5);
    &:hover {
      outline: none;
      cursor: default;
    }
  }
</style>
