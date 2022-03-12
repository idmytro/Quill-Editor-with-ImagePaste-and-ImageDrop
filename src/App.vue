<template>
  <div id="app">
    <quill-editor v-model="text" :options="options"></quill-editor>
  </div>
</template>

<script>
import VueQuillEditor from 'vue-quill-editor';
import Quill from 'quill';
import { ImageDrop } from 'quill-image-drop-module';
import ImagePaste from './quill/imagePasteClass';
import ImageResize from './quill/ResizeImage/ImageResize';

Quill.register('modules/imageDrop', ImageDrop);
Quill.register('modules/imagePaste', ImagePaste);
Quill.register('modules/imageResize', ImageResize);

const options = {
  placeholder: 'Inserte el texto aquí..',
  modules: {
    // imageDrop: true,
    imagePaste: true,
    toolbar: [
      ['bold', 'italic', 'underline', 'strike'],
      ['blockquote', 'code-block'],
      [{ header: 1 }, { header: 2 }],
      [{ list: 'ordered' }, { list: 'bullet' }],
      [{ script: 'sub' }, { script: 'super' }],
      [{ indent: '-1' }, { indent: '+1' }],
      [{ direction: 'rtl' }],
      [{ size: ['small', false, 'large', 'huge'] }],
      [{ header: [1, 2, 3, 4, 5, 6, false] }],
      [{ font: [] }],
      [{ color: [] }, { background: [] }],
      [{ align: [] }],
      ['clean'],
      ['link', 'image', 'video'],
      ['template-partediario'],
    ],
    imageResize: {
      displayStyles: {
        backgroundColor: 'black',
        border: 'none',
        color: 'white',
      },
      modules: ['Resize', 'DisplaySize', 'Toolbar'],
    },
  },
};

export default {
  name: 'App',
  components: {
    'quill-editor': VueQuillEditor.quillEditor,
  },
  data() {
    return {
      text: '',
      options,
    };
  },
};
</script>
