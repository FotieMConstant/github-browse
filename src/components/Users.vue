<template>
  <v-app>
    <v-card max-width="450" class="mx-auto">
      <v-list three-line>
        <span>Users</span>
        <div v-for="user in users" :key="user">
          <v-subheader></v-subheader>

          <v-divider></v-divider>

          <v-list-item>
            <v-list-item-avatar>
              <v-img :src="user.avatar_url"></v-img>
            </v-list-item-avatar>

            <v-list-item-content>
              <v-list-item-title v-html="user.login"></v-list-item-title>
              <v-list-item-subtitle
                v-html="user.repos_url"
              ></v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </div>
      </v-list>
    </v-card>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    showLoader: true,
    items: [
      { header: "Today" },
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/1.jpg",
        title: "Brunch this weekend?",
        subtitle: `<span class="text--primary">Ali Connors</span> &mdash; I'll be in your neighborhood doing errands this weekend. Do you want to hang out?`,
      },
      { divider: true, inset: true },
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
        title: 'Summer BBQ <span class="grey--text text--lighten-1">4</span>',
        subtitle: `<span class="text--primary">to Alex, Scott, Jennifer</span> &mdash; Wish I could come, but I'm out of town this weekend.`,
      },
      { divider: true, inset: true },
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/3.jpg",
        title: "Oui oui",
        subtitle:
          '<span class="text--primary">Sandra Adams</span> &mdash; Do you have Paris recommendations? Have you ever been?',
      },
      { divider: true, inset: true },
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/4.jpg",
        title: "Birthday gift",
        subtitle:
          '<span class="text--primary">Trevor Hansen</span> &mdash; Have any ideas about what we should get Heidi for her birthday?',
      },
      { divider: true, inset: true },
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/5.jpg",
        title: "Recipe to try",
        subtitle:
          '<span class="text--primary">Britta Holt</span> &mdash; We should eat this: Grate, Squash, Corn, and tomatillo Tacos.',
      },
    ],
    users: null,
  }),
  mounted: function () {
    const url = `https://api.github.com/users`;

    this.axios
      .get(url)
      .then((response) => {
        this.users = response.data;
        console.log(response.data);
      })
      .catch((error) => {
        console.log(error);
      })
      .finally(() => (this.showLoader = false));
    // End of request
  },
};
</script>