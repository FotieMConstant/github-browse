<template>
  <div class="home">
    <Search />
    <Users />
  </div>
</template>

<script>
// @ is an alias to /src
import Users from "@/components/Users";
import Search from "@/components/Search";

export default {
  name: "Home",
  components: {
    Users,
    Search,
  },
};
</script>
