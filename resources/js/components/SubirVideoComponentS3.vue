
<style src="../../../public/plugins/dropzone/dist/dropzone.css"></style>


<template>
    <div class="row">
                                <div class="col-12">
                                    <div class="card">
                                        <div class="card-body">
            
                                            <h4 class="mt-0 header-title">Dropzone</h4>
                                            <p class="text-muted m-b-30">DropzoneJS is an open source library
                                                that provides drag’n’drop file uploads with image previews.
                                            </p>
            
                                            <div class="m-b-30">



                                                <vue-dropzone id="drop2" :options="dropOptions" >
                                                    

                                                </vue-dropzone>

                            


                                            </div>
            
                                            <div class="text-center m-t-15">
                                                <button type="button" class="btn btn-primary waves-effect waves-light">Send Files</button>
                                            </div>
                                        </div>
                                    </div>
                                </div> <!-- end col -->

                                <div class="col-12">
                                    <div class="card">
                                        <div class="card-body">
            
                                        <div class="table-responsive">
                                                                <table class="table table-striped mb-0">
                    
                                                                    <thead>
                                                                        <tr>

                                                                            <th>Nombre del Vídeo</th>
                                                                            <th>Tamaño</th>
                                                                            <th>Progreso</th>

                                                                        </tr>
                                                                    </thead>
                                                                    <tbody>
                                                                        <tr>
                                                                            <th scope="row">generacion_perdida.mp4</th>
                                                                            <td> 404 MB</td>
                                                                            <td><div class="progress m-b-15">
                                                <div class="progress-bar progress-bar-striped bg-primary" role="progressbar" style="width: 25%" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100"></div>
                                            </div></td>
                                                                        </tr>
                                                                        
                                                                        
                                                    </tbody>
                                                </table>
                                            </div>
                                        </div>
                                    </div>
                                </div> <!-- end col -->
                            </div> <!-- end row -->

                            
</template>

<script>
 
    import vueDropzone from "vue2-dropzone";
    import SparkMD5 from 'spark-md5';


    export default {

        data: () => ({
            dropOptions: {
                url: "/uploadFilesS3",
                paramName: 'file2',
                acceptedFiles: ".mp4",
                maxFilesize: 600000,
                addRemoveLinks: true,
                headers: {
                    "X-CSRF-TOKEN": document.head.querySelector("[name=csrf-token]").content
                },
            },  //drop options

             awss3: {
                    signingURL: 'http://localhost:3000/attachments', //Where you will get signed url
                    headers: {},
                    params : {},
                    sendFileToServer : true //If you want to upload file to your server along with s3
            }


        }),    //data


        components: {
            vueDropzone
        }



    };
</script>






