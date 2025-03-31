<template>
  <q-btn round flat icon="account_circle">
    <q-menu fit anchor="bottom right" self="top right">
      <q-list style="min-width: 150px">
        <q-item clickable v-close-popup>
          <q-item-section avatar>
            <q-icon name="person" />
          </q-item-section>
          <q-item-section>Profil</q-item-section>
        </q-item>

        <q-item clickable v-close-popup>
          <q-item-section avatar>
            <q-icon name="settings" />
          </q-item-section>
          <q-item-section>Sozlamalar</q-item-section>
        </q-item>

        <q-separator />

        <q-item clickable v-close-popup>
          <q-item-section avatar>
            <q-icon name="logout" />
          </q-item-section>
          <q-item-section>Chiqish</q-item-section>
        </q-item>
      </q-list>
    </q-menu>
  </q-btn>
</template>

<script>
export default {
  name: "ProfileDropdown",
};
</script>
