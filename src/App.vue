<script setup>
import Card from "./components/Card.vue";
import Footer from "./components/Footer.vue"
import Button from "./components/Button.vue"
import { ref, onMounted } from "vue";

// Ref objects are mutable and reactive. Can set ref.value to allow values to change
const quote = ref("");
const character = ref("");
const disabled = ref(false);
const isLoading = ref(false);

//  Get quote and character data from local JSON database asynchronously
async function getQuote() { 
  try {
    isLoading.value = true;
    character.value = " ";
    quote.value = "Loading ...";

    // Use await new Promise(resolve => setTimeout(resolve, 2000)) to test loading state

    const response = await fetch("/database/quotesDatabase.json");
    const data = await response.json();

    // Math.floor() function rounds this number down to the nearest integer to ensure it's a valid number
    const selectedQuote = Math.floor(Math.random() * data.quotes.length);
    quote.value = data.quotes[selectedQuote].quote, 
    character.value = data.quotes[selectedQuote].character;
  } catch(err) {   
      quote.value = "Sorry, we're having trouble finding quotes right now.";
      console.log(err);
  }
  // Ensure loading state is updated in both success and error cases
  isLoading.value = false;
}

// Once the component is loaded, call the getQuote function. Allows page to fetch the data from the getQuote function on page refresh
onMounted(() => {
  getQuote();
})

// Image spin function. If const disabled is true, cause the image to spin for 600 ms and revert disabled equal to false
function imgSpin() {
  disabled.value = true;
  setTimeout(() => {
    disabled.value = false;
  }, 600);
}
</script>

<template>
  <main>
    <!-- Pass character and quote props to Card component -->
    <Card :subhead="character" :title="quote"></Card>

    <!-- Call the img spin class at the button and set it to disabled so that onclick generates the imgSpin function and generates a random quote -->
    <Button :class="{ spin: disabled }" @click="imgSpin(),getQuote()"></Button>
  </main>
  <Footer></Footer>
</template>
