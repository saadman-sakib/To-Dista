<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <v-list>
        <v-list-item>
          <v-list-item-avatar>
            <v-img src="https://cdn.vuetifyjs.com/images/john.png"></v-img>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="title"> Saadman Sakib </v-list-item-title>
            <v-list-item-subtitle>khubsadman@gmail.com</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-list nav dense>
        <v-list-item-group v-model="selectedItem" color="primary">
          <v-text-field
          placeholder="Search"
          :append-icon="'mdi-magnify'"
          @click:append="dialog = true"
          filled
          rounded
          dense
        ></v-text-field>
          <v-list-item v-for="(item, i) in items" :key="i">
            <v-list-item-icon>
              <v-icon v-text="item.icon"></v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title v-text="item.text"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
        <br />
        <div class="tab-outline">
          <v-tabs class="tab" fixed-tabs>
            <v-tab>Catagories</v-tab>
            <v-tab>Tags</v-tab>
            <v-tab-item>
              <v-list-item-group class="tab-itm" no-action sub-group>
                <v-list-item v-for="([title,], i) in cruds" :key="i" link>
                  <v-list-item-icon>
                    <v-icon >mdi-format-list-bulleted</v-icon>
                  </v-list-item-icon>
                  <v-list-item-title v-text="title"></v-list-item-title>
                </v-list-item>
                <v-list-item link>
                  <v-list-item-icon>
                    <v-icon >mdi-plus-box-multiple</v-icon>
                  </v-list-item-icon>
                  <v-list-item-title>Add Catagory</v-list-item-title>
                </v-list-item>
              </v-list-item-group>
            </v-tab-item>

            <v-tab-item>
              <v-list-item-group class="tab-itm" no-action sub-group>
                <v-list-item v-for="([title,], i) in admins" :key="i" link>
                  <v-list-item-icon>
                    <v-icon >mdi-tag</v-icon>
                  </v-list-item-icon>
                  <v-list-item-title v-text="title"></v-list-item-title>
                </v-list-item>
                <v-list-item link>
                  <v-list-item-icon>
                    <v-icon >mdi-plus-box-multiple</v-icon>
                  </v-list-item-icon>
                  <v-list-item-title>Add Tag</v-list-item-title>
                </v-list-item>
              </v-list-item-group>
            </v-tab-item>
          </v-tabs>
        </div>
        <br />
        <v-list-group :value="false" prepend-icon="mdi-account-circle">
          <template v-slot:activator>
            <v-list-item-title><h1>Users</h1></v-list-item-title>
          </template>

          <v-list-group :value="false" no-action sub-group>
            <template v-slot:activator>
              <v-list-item-content>
                <v-list-item-title>Admin</v-list-item-title>
              </v-list-item-content>
            </template>

            <v-list-item v-for="([title, icon], i) in admins" :key="i" link>
              <v-list-item-title>{{ title }}</v-list-item-title>
              <v-list-item-icon>
                <v-icon v-text="icon"></v-icon>
              </v-list-item-icon>
            </v-list-item>
          </v-list-group>

          <v-list-group no-action sub-group>
            <template v-slot:activator>
              <v-list-item-content>
                <v-list-item-title>Actions</v-list-item-title>
              </v-list-item-content>
            </template>

            <v-list-item v-for="([title, icon], i) in cruds" :key="i" link>
              <v-list-item-title v-text="title"></v-list-item-title>

              <v-list-item-icon>
                <v-icon v-text="icon"></v-icon>
              </v-list-item-icon>
            </v-list-item>
          </v-list-group>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <img style="margin-right:10px" src="@/assets/icon.png" height="25px" />
      <v-toolbar-title> To-Dista </v-toolbar-title>
    </v-app-bar>
    <br />
    <br />
    <br />
    <div class="add">
      <v-text-field
        placeholder="What do you want to add?"
        :append-icon="'mdi-plus-circle'"
        @click:append="dialog = true"
        filled
        rounded
        dense
      ></v-text-field>
    </div>
    <div class="card-holder">
      <v-card
        v-for="([title, , n], i) in cruds"
        :key="i"
        elevation="7"
        outlined
        shaped
        class="card"
        color=""
      >
        <v-list-item three-line>
          <v-list-item-content>
            <v-list-item-title class="headline mb-1">
              <v-icon v-if="i % 3 == 0" color="success" left>mdi-check-circle</v-icon>
              <v-icon v-else color="orange" left>mdi-alert</v-icon>
              {{ title }}
              <!-- <v-chip v-if="i % 3 == 0" class="ma-2" color="success" outlined>
                <v-icon left> mdi-check </v-icon>
                Done
              </v-chip>
              <v-chip v-else class="ma-2" color="error" outlined>
                <v-icon left> mdi-alert-circle </v-icon>
                Due
              </v-chip> -->
            </v-list-item-title>
            <v-list-item-subtitle
              >Greyhound divisely hello coldly
              fonwderfully</v-list-item-subtitle
            >
          </v-list-item-content>
        </v-list-item>

        <br />
        <div class="justify">
          <v-card-actions>
            <v-btn text color="primary" @click="dialog = true">
              Detail
            </v-btn>
          </v-card-actions>
          <v-chip outlined>
            <div v-for="x in n" :key="x">
              <v-avatar size="20" class="avatar">
                <img
                  :src="
                    `https://randomuser.me/api/portraits/women/` +
                    x +
                    i +
                    `.jpg`
                  "
                  alt="John"
                />
              </v-avatar>
            </div>
          </v-chip>
        </div>
      </v-card>
    </div>
    <v-row justify="center">
      <v-dialog v-model="dialog" width="600px">
        <v-card>
          <v-card-title>
            <span class="headline">Use Google's location service?</span>
          </v-card-title>
          <v-card-text>
            Lorem ipsum dolor sit amet, semper quis, sapien id natoque elit.
            Nostra urna at, magna at neque sed sed ante imperdiet, dolor mauris
            cursus velit, velit non, sem nec. Volutpat sem ridiculus placerat
            leo, augue in, duis erat proin condimentum in a eget, sed fermentum
            sed vestibulum varius ac, vestibulum volutpat orci ut elit eget
            tortor. Ultrices nascetur nulla gravida ante arcu. Pharetra rhoncus
            morbi ipsum, nunc tempor debitis, ipsum pellentesque, vitae id quam
            ut mauris dui tempor, aptent non. Quisque turpis. Phasellus quis
            lectus luctus orci eget rhoncus. Amet donec vestibulum mattis
            commodo, nulla aliquet, nibh praesent, elementum nulla. Sit lacus
            pharetra tempus magna neque pellentesque, nulla vel erat. Justo ex
            quisque nulla accusamus venenatis, sed quis. Nibh phasellus gravida
            metus in, fusce aenean ut erat commodo eros. Ut turpis, dui integer,
            nonummy pede placeat nec in sit leo. Faucibus porttitor illo taciti
            odio, amet viverra scelerisque quis quis et tortor, curabitur morbi
            a. Enim tempor at, rutrum elit condimentum, amet rutrum vitae tempor
            torquent nunc. Praesent vestibulum integer maxime felis.
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="green darken-1" text @click="dialog = false">
              Disagree
            </v-btn>
            <v-btn color="green darken-1" text @click="dialog = false">
              Agree
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
    <br />
    <br />
    <br />
    <v-footer dark padless>
      <v-card width="100%" flat tile class="white--text text-center">
        <v-card-text>
          <v-btn
            v-for="icon in icons"
            :key="icon"
            class="mx-4 white--text"
            icon
          >
            <v-icon size="24px">
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text class="white--text">
          {{ new Date().getFullYear() }} — <strong>@copyright</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>


<script>
export default {
  data() {
    return {
      drawer: null,
      selectedItem: 0,
      items: [
        { text: "Dashboard", icon: "mdi-view-dashboard" },
        { text: "All Tasks", icon: "mdi-clipboard-text-outline" },
        { text: "Today", icon: "mdi-clock-time-five-outline" },
        { text: "Upcoming", icon: "mdi-timer-sand" },
        { text: "Calender View", icon: "mdi-calendar" },
        { text: "Completed", icon: "mdi-checkbox-marked-circle-outline" },
        { text: "Trash", icon: "mdi-trash-can-outline" },
      ],
      admins: [
        ["Management", "mdi-account-multiple-outline"],
        ["Settings", "mdi-cog-outline"],
      ],
      cruds: [
        ["Create", "mdi-plus-outline", 3],
        ["Read", "mdi-file-outline", 2],
        ["Update", "mdi-update", 4],
        ["Delete", "mdi-delete", 3],
      ],
      dialog: false,
      icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"],
    };
  },
};
</script>

<style scoped>
.card {
  margin: 30px;
  margin-left: 5%;
  margin-right: 5%;
  padding: 20px;
  max-width: 700px;
  /* min-width: 400px; */
}

.avatar {
  border: solid 2px;
}

.justify {
  display: flex;
  justify-content: space-between;
}

.tab-itm {
  background: rgb(54, 54, 54);
}

.tab {
  border-radius: 5px;
}
.tab-outline {
  border: 0.1px solid rgb(124, 124, 124);
  border-radius: 5px;
}
.add {
  margin-left: 5%;
  margin-right: 5%;
  max-width: 700px;
  /* min-width: 400px; */
}
</style>