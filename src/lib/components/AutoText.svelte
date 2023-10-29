<script>
    let currentText = '';
    const fullText = 'a spiderman walking';
    let index = 0;
  
    function typeText() {
      if (index < fullText.length) {
        currentText += fullText.charAt(index);
        index++;
        setTimeout(typeText, 100); // Adjust the speed by changing the timeout value
      }
    }
  
    // Start typing as soon as the component is mounted
    import { onMount } from 'svelte';
    onMount(() => {
      typeText();
    });
  </script>

  <div>
    <input type="text" value={currentText} readonly />
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
      transform: translateX(-50%); /* Adjusted */
      border-radius: 5px;
      background-color: rgba(13, 19, 32, 0.5);
      &:hover {
        outline: none;
        cursor: default;
      }
    }
  </style>
  