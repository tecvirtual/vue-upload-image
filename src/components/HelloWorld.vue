<template>
    <div>
        <vue-dropzone ref="myVueDropzone" :options="dropzoneOptions" v-on:vdropzone-sending="sendingEvent" v-on:vdropzone-removed-file="deleteImage" :id="titulo"></vue-dropzone>
    </div>
</template>

<script>
    import vue2Dropzone from 'vue2-dropzone'
    import 'vue2-dropzone/dist/vue2Dropzone.min.css'
    export default {
        name: "Upload",
        props: ['titulo', 'tipo','cantidad','idactivity'],
        components: {
            vueDropzone: vue2Dropzone
        },
        mounted() {

        },
        data() {
            return {
                user_id: '1',
                direccion2: '',
                portada1: '',
                dropzoneOptions: {
                    url: 'https://httpbin.org/post',
                    thumbnailWidth: 150,
                    maxFilesize: 5.5,
                    maxFiles: this.cantidad,
                    headers: {
                       // "X-CSRF-TOKEN": document.head.querySelector("[name=csrf-token]").content,
                    },
                    addRemoveLinks: true
                    //addRemoveLinks: true
                },
                titulo_galeria: '',
                images : []
            }
        },
        methods: {
            sendingEvent (file, xhr, formData) {
                //formData.append('user_id', this.user_id);
                formData.append('activity_id', this.idactivity);
                formData.append('tipo', this.tipo);
                formData.append('titulo', this.titulo);
            },
            deleteImage(file) {
                const xhrJSON = JSON.parse(file.xhr.response);
                this.axios
                    .delete('/uploads', {
                        data: {
                            imageName: xhrJSON.filename,
                        },
                    })
                    .catch(err => {
                        console.log(err);
                    });
            },
        },
    }
</script>

<style scoped>

</style>