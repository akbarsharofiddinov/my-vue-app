<template>
  <q-header elevated class="bg-primary text-white" style="padding: 10px 0">
    <q-toolbar>
      <q-btn
        dense
        flat
        round
        icon="menu"
        @click="
          () => {
            $emit('toggle-drawer');
          }
        "
      />
      <q-toolbar-title>
        <!-- Space -->
      </q-toolbar-title>

      <ProfileDropdown />
    </q-toolbar>
  </q-header>
</template>

<script>
import ProfileDropdown from "../UI/ProfileDropDown.vue";
export default {
  components: { ProfileDropdown },
  emits: ["toggle-drawer"],
};
</script>
