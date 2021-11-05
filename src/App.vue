<template>
  <div class="container">
    <h1>Rick and Morty</h1>
    <FilterByStatusComponent/>
    <FilterByNameComponent/>
    <ListCharacters />
  </div>
</template>

<script>
import ListCharacters from "@/components/ListCharactersComponent";
import FilterByStatusComponent from "@/components/FilterByStatusComponent";
import FilterByNameComponent from '@/components/FilterByNameComponent';

export default {
  name: "App",
  components: {
    FilterByStatusComponent,
    FilterByNameComponent,
    ListCharacters
  },
};
</script>

<style lang="scss">
:root {
  --background-body: #24282f;
  --background-card: #3c3e44;
  --text-white: #ffffff;
  --text-gray: #c0c0c0;
  --text-orange: #ff9800;
}
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  background-color: var(--background-body);
  color: var(--text-white);
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
#app{
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px;
}
h1 {
  margin-bottom: 3rem;
  text-align: center;
}
.container{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 10px;
}
img {
  width: 100%;
}
</style>
