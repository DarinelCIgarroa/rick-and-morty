<template>
  <section>
    <div class="characters" v-if="characters.length>0">
      <div
        class="characters__item"
        v-for="character in characters"
        :key="character"
      >
        <card-character-component  :character="character"/>
      </div>
    </div>
    <div v-else>
      <h1 class="unknown">Sin resultados</h1>
    </div>
  </section>
</template>

<script>
import { computed, onMounted } from "vue";
import { useStore } from "vuex";
import CardCharacterComponent from "@/components/CardCharacterComponent";

export default {
  components: {
    CardCharacterComponent
  },
  setup() {
    const store = useStore();

    const characters = computed(() => {
      return store.state.charactersFilter;
    });
    
    onMounted(() => {
      store.dispatch("getCharacters");
    });

    return {
      characters,
    };
  },
};
</script>

<style lang="scss">
.characters {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 3rem;
  margin: 3rem 0;
}
.unknown{
  margin: 50px 0px;
  font-size: 50px;
}
</style>