<template>
  <div class="hello">
    <input
      type="file"
      ref="file"
      @click="
        (e) => {
          e.target.value = '';
        }
      "
      @change="selectedFile"
      multiple
    />
  </div>
</template>

<script>
import { saveAs } from "file-saver";
export default {
  name: "FileSelector",
  methods: {
    selectedFile(e) {
      let files = e.target.files || e.dataTransfer.files;

      this.fileProcessing(files);
    },
    // **********************************************
    // * ファイル処理共通
    // **********************************************
    fileProcessing(files) {
      var MyBlobBuilder = function () {
        this.parts = [];
      };

      MyBlobBuilder.prototype.append = function (part) {
        this.parts.push(part);
        this.blob = undefined; // Invalidate the blob
      };

      MyBlobBuilder.prototype.getBlob = function () {
        if (!this.blob) {
          this.blob = new Blob(this.parts, {
            type: "application/octet-stream",
          });
        }
        return this.blob;
      };
      var myBlobBuilder = new MyBlobBuilder();
      files.forEach((e) => {
        myBlobBuilder.append(e);
      });
      saveAs(myBlobBuilder.getBlob(), "test.zip");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
