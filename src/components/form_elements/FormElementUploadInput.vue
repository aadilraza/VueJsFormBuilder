<template>
  <div>
    <!-- <el-button type="primary" class="form__button">{{ currentField.buttonText }}</el-button> -->
    <el-button class="form__button" @click="onPickFile">
      {{ currentField.buttonText }}
    </el-button>
    <input
      type="file"
      style="display: none"
      ref="fileInput"
      accept="image/*"
      @change="onFilePicked"
    />
  </div>
</template>

<script>
export default {
  name: "Upload",
  props: ["currentField"],
  methods: {
    onPickFile() {
      console.log("file upload button clicked");
      this.$refs.fileInput.click();
    },
    onFilePicked(event) {
      debugger;
      const files = event.target.files;
      let filename = files[0].name;
      const fileReader = new FileReader();
      fileReader.addEventListener("load", () => {
        this.imageUrl = fileReader.result;
      });
      fileReader.readAsDataURL(files[0]);
      this.image = files[0];
    },
  },
};
</script>
