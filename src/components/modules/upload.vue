<template>
    <transition name="el-zoom-in-top">
        <picture-input
        ref="pictureInput"
        @change="onChanged"
        @remove="onRemoved"
        :width="500"
        :removable="true"
        removeButtonClass="ui red button"
        :height="500"
        accept="image/jpeg, image/png, image/gif"
        buttonClass="btn-primary"
        :customStrings="{
        upload: '<h1>Upload it!</h1>',
        drag: 'Drag and drop your image here'}">
        </picture-input>
            <button @click="attemptUpload" v-bind:class="{ disabled: !image }">
                Upload
            </button>
    </transition>
</template>
<script>
  import axios from 'axios'
  import FormDataPost from '/upload'
  export default function (url, file, name = 'avatar') {
  if (typeof url !== 'string') {
    throw new TypeError(`Expected a string, got ${typeof url}`);
  }

  // You can add checks to ensure the url is valid, if you wish

  const formData = new FormData();
  formData.append(name, file);
  const config = {
    headers: {
      'content-type': 'multipart/form-data'
    }
  }
  return axios.post(url, formData, config)
  FormDataPost('http://localhost:8001/user/picture', image)
  .then(response=>{
    console.log("Uploaded picture successfully");
  })
  .catch(err=>{
    console.error(err);
  })
  methods: {
  onChanged () {
    console.log("New picture loaded");
    if (this.$refs.pictureInput.file) {
      this.image = this.$refs.pictureInput.file;
    } else {
      console.log("Old browser. No support for Filereader API");
    }
  }
  onRemoved () {
    this.image = '';
  }
  attemptUpload() {
    if (this.image){
      FormDataPost('http://localhost:8001/user/picture', this.image)
        .then(response=>{
          if (response.data.success){
            this.image = '';
            console.log("Image uploaded successfully ✨");
          }
        })
        .catch(err=>{
          console.error(err);
        })
      }
    }
  }
}
</script>
