<template>
  <q-layout view="lHh lpR fFf" v-if="isMini">
    <Header @toggle-drawer="toggleLeftDrawer" />
    <Sidebar v-model="isMini" :mini="leftDrawerOpen" @enable-drawer="enableLeftDrawer" />

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>

  <q-layout view="lHh lpR fFf" v-if="!isMini">
    <Header @toggle-drawer="toggleLeftDrawer" />
    <Sidebar v-model="leftDrawerOpen" :mini="isMini" />

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from "vue";
import Header from "./components/Header.vue";
import Sidebar from "./components/Sidebar.vue";

export default {
  components: {
    Header,
    Sidebar,
  },

  setup() {
    // Sidebar ochiq yoki yopiq holatini saqlash
    const leftDrawerOpen = ref(false);

    // Mini rejim uchun o'zgaruvchi
    const isMini = ref(false);

    // Qurilma turi (desktop yoki mobile)
    const behavior = ref("desktop");

    // Sidebarni toggling qilish
    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value;
    };

    const enableLeftDrawer = () => {
      leftDrawerOpen.value = false;
    };

    // Ekran o‘lchami bo‘yicha mini rejimni o‘zgartirish
    const checkScreenSize = () => {
      if (window.innerWidth <= 500) {
        isMini.value = false; // Mobil qurilmalarda mini rejim yo‘q
        behavior.value = "mobile";
      } else {
        isMini.value = true; // Katta ekranlarda mini rejim mavjud
        behavior.value = "desktop";
      }
    };

    // Ekran o'lchami o'zgarganda tekshirish
    window.addEventListener("resize", checkScreenSize);
    checkScreenSize(); // Dastlabki yuklanishda chaqirish

    return {
      leftDrawerOpen,
      isMini,
      behavior,
      toggleLeftDrawer,
      enableLeftDrawer,
    };
  },
};
</script>
