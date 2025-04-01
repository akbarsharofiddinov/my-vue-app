<!-- <template>
  <q-drawer show-if-above v-model="drawerOpen" side="left" elevated>
    <div
      class="logo bg-primary text-white"
      style="padding: 10px; text-align: center"
    >
      <q-avatar>
        <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" />
      </q-avatar>
    </div>

    <q-list>
      <q-item clickable>
        <q-item-section>Сотрудники</q-item-section>
      </q-item>
      <q-expansion-item expand-separator label="Товары">
        <q-item clickable v-ripple>
          <q-item-section>Element 1</q-item-section>
        </q-item>
        <q-item clickable v-ripple>
          <q-item-section>Element 2</q-item-section>
        </q-item>
      </q-expansion-item>
      <q-item clickable>
        <q-item-section>Контрагенты</q-item-section>
      </q-item>
    </q-list>
  </q-drawer>
</template>

<script>
export default {
  props: {
    modelValue: Boolean,
  },
  emits: ["update:modelValue"],
  computed: {
    drawerOpen: {
      get() {
        return this.modelValue;
      },
      set(value) {
        this.$emit("update:modelValue", value);
      },
    },
  },
};
</script> -->

<template>
  <q-drawer
    :mini="mini"
    :width="200"
    :class="$q.dark.isActive ? 'bg-grey-9' : 'bg-grey-3'"
    elevated
  >
    <q-scroll-area class="fit" :horizontal-thumb-style="{ opacity: 0 }">
      <q-toolbar-title
        class="bg-primary text-white"
        style="
          padding: 10px;
          display: flex;
          align-items: center;
          height: 70px;
          gap: 10px;
        "
      >
        <img
          src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg"
          style="max-width: 40px; max-height: 40px; object-fit: contain"
        />
        <q-item-section>Title</q-item-section>
      </q-toolbar-title>
      <q-list padding>
        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="inbox" />
          </q-item-section>
          <q-item-section> Inbox </q-item-section>
        </q-item>

        <q-item active clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="star" />
          </q-item-section>
          <q-item-section> Star </q-item-section>
        </q-item>

        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="send" />
          </q-item-section>
          <q-item-section> Send </q-item-section>
        </q-item>

        <q-expansion-item
          expand-separator
          icon="folder_open"
          label="Товары"
          v-if="!mini"
        >
          <q-item clickable v-ripple>
            <q-item-section>Element 1</q-item-section>
          </q-item>
          <q-item clickable v-ripple>
            <q-item-section>Element 2</q-item-section>
          </q-item>
        </q-expansion-item>

        <q-item clickable v-ripple v-if="mini">
          <q-item-section avatar>
            <q-icon name="folder_open" />
          </q-item-section>
          <q-item-section>Basic Menu</q-item-section>
          <q-menu :offset="[-50, 0]" style="width: 200px">
            <q-list style="min-width: 100px; max-width: 100%; width: 100">
              <q-item clickable v-close-popup>
                <q-item-section>Element 1</q-item-section>
              </q-item>
              <q-separator />
              <q-item clickable v-close-popup>
                <q-item-section>Element 2</q-item-section>
              </q-item>
            </q-list>
          </q-menu>
        </q-item>

        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="drafts" />
          </q-item-section>
          <q-item-section> Drafts </q-item-section>
        </q-item>
      </q-list>
    </q-scroll-area>
  </q-drawer>
</template>

<style lang="scss" scoped>
.q-btn {
  background: transparent !important;
  box-shadow: none !important;

  &::after,
  &::before {
    background: transparent !important;
    box-shadow: none !important;
  }
}

.q-btn {
  border: none !important;
  box-shadow: none !important;

  &::after,
  &::before {
    border: none !important;
    box-shadow: none !important;
  }
}
</style>

<script>
export default {
  props: {
    mini: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    drawerOpen: {
      get() {
        console.log(this.modelValue);
        return this.modelValue;
      },
      set(value) {
        this.$emit("update:modelValue", value);
      },
    },
    isDrawerMini: {
      get() {
        return this.isMini;
      },
      set(value) {
        this.$emit("update:isMini", value);
      },
    },
  },
};
</script>
