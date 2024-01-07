<template>
  <div>
    <base-button mode="filled" rounded>Add</base-button>
    <base-button mode="filled" append-icon="add" rounded>Add</base-button>
    <base-button mode="filled" disabled-btn rounded>Add</base-button>
    <base-button mode="filled" disabled-btn append-icon="add" rounded>Add</base-button>
  </div>
  <div>
    <base-button mode="outline">Edit</base-button>
    <base-button mode="outline" append-icon="edit">Edit</base-button>
    <base-button mode="outline" disabled-btn>Edit</base-button>
    <base-button mode="outline" disabled-btn append-icon="edit">Edit</base-button>
  </div>
  <div>
    <base-button mode="text">Attach</base-button>
    <base-button mode="text" prepend-icon="attach">Attach</base-button>
    <base-button mode="text" disabled-btn>Attach</base-button>
    <base-button mode="text" disabled-btn prepend-icon="attach">Attach</base-button>
  </div>
  <div>
    <base-button mode="elevated" rounded>Back</base-button>
    <base-button mode="elevated" prepend-icon="back" rounded>Back</base-button>
    <base-button mode="elevated" disabled-btn rounded>Back</base-button>
    <base-button mode="elevated" disabled-btn prepend-icon="back" rounded>Back</base-button>
  </div>
  <div>
    <base-button mode="tonal" rounded>Forward</base-button>
    <base-button mode="tonal" prepend-icon="forward" rounded>Forward</base-button>
    <base-button mode="tonal" disabled-btn rounded>Forward</base-button>
    <base-button mode="tonal" disabled-btn prepend-icon="forward" rounded>Forward</base-button>
  </div>
</template>

<script setup>
import BaseButton from "@/ui/BaseButton.vue";
</script>

<style scoped>

div {
  margin-bottom: 15px;
}

</style>
