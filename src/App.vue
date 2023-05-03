<script setup>
import Card from "./components/Card.vue";
import Footer from "./components/Footer.vue"
import Button from "./components/Button.vue"
import { ref, onMounted } from "vue";

// Ref objects are mutable and reactive. Can set ref.value to allow values to change
const quote = ref("");
const character = ref("");
const characterColor = ref("");
const characterImage = ref("");
const characterIcon = ref("");
const iconName = ref("");
const disabled = ref(false);
const isLoading = ref(false);

//  Get quote and character data from local JSON database asynchronously
async function getQuote() { 
  try {
    // Create a loading state and use await new Promise(resolve => setTimeout(resolve, 2000)) to test
    isLoading.value = true;
    character.value = " ";
    quote.value = "Loading ...";

    // Fetch quotes and characters data from their respective local JSON databases
    const quotesResponse = await fetch("/data/quotesDatabase.json");
    const charactersResponse = await fetch("/data/charactersDatabase.json");

    const quotesData = await quotesResponse.json();
    const charactersData = await charactersResponse.json();

    // Randomly choose quote. Define the chosen quote, characterId, then use selectedCharacterId (foreign key) to access the characters database
    const randomizeQuote = Math.floor(Math.random() * quotesData.quotes.length);
    const selectedQuote = quotesData.quotes[randomizeQuote];
    const selectedCharacterId = selectedQuote.characterId;
    const selectedCharacter = charactersData.characters.find((character) => character.characterId === selectedCharacterId);

    // If the quote and character match, set the values of quote, character, image, and color equal to that selected quote and character. Then set the css variable --character-color to the characterColor and --character-image to characterImage
    if (selectedQuote && selectedCharacter) {
      quote.value = selectedQuote.quote;
      character.value = selectedCharacter.characterName;
      characterColor.value = selectedCharacter.characterColor;
      characterImage.value = selectedCharacter.characterImage;
      characterIcon.value = selectedCharacter.characterIcon;
      iconName.value = selectedCharacter.iconName;
      document.documentElement.style.setProperty('--character-color', characterColor.value);
    }
    isLoading.value = false;

    // Error handling if quotes aren't available
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
    <!-- Pass props to Card component -->
    <Card :subhead="character" :title="quote" :avatar="characterImage" :icon="characterIcon" :iconName="iconName"></Card>

    <!-- Call the img spin class at the button and set it to disabled so that onclick generates the imgSpin function and generates a random quote -->
    <Button :class="{ spin: disabled }" @click="imgSpin(),getQuote()"></Button>
  </main>
  <Footer></Footer>
</template>
