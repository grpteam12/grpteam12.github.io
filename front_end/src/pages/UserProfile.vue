<template>
  <div class="content">
    <div class="md-layout">
      <div class="md-layout-item md-medium-size-400 md-size-500">
        <edit-profile-form data-background-color="green"> </edit-profile-form>
      </div>
    </div>
  </div>
</template>

<script>
import { EditProfileForm } from "@/pages";

export default {
  components: {
    EditProfileForm,
  },
};
</script>
