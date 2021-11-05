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
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.unknown{
  margin: 50px 0px;
  font-size: 50px;
}
.characters__item{
  margin: 20px;
}
</style>