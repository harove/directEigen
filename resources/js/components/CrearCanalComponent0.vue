<template>
    <div class="row">
        <div class="col-lg-6">
            <div class="card">
                <div class="card-body">

                    <h4 class="mt-0 header-title">Crear Canal</h4>
                    <p class="text-muted m-b-30 ">Parsley is a javascript form validation
                        library. It helps you provide your users with feedback on their form
                        submission before sending it to your server.</p>

                        <div class="form-group">
                            <label>Nombre del Canal</label>
                            <input type="text" v-model="nombre_canal" class="form-control" required placeholder="Ingresar nombre del canal"/>
                        </div>

                        <!-- <div class="form-group">
                            <label>Subir Logo del Player</label>
                            <input type="file" class="filestyle" data-buttonname="btn-secondary">
                        </div>
                        
                        <div class="form-group">
                            <label class="control-label">Selección tamaño de player</label>
                            <select class="form-control select2">
                                <option>Seleccionar</option>
                                <optgroup label="Selección en pixeles">
                                    <option value="AK">512 x 288</option>
                                    <option value="HI">640 x 360</option>
                                    <option value="HI">768 x 432</option>
                                    <option value="HI">960 x 540</option>
                                    <option value="HI">1280 x 720</option>
                                    <option value="HI">1920 x 1080</option>
                                </optgroup>
                                
                            </select>
                        </div>

                        <div class="form-group">
                            <label>Subir fondo del Player</label>
                            <input type="file" class="filestyle" data-buttonname="btn-secondary">
                        </div> -->
                        
                        <div class="form-group">
                            <div>
                                <button type="submit" @click='crearCanal()' class="btn btn-primary waves-effect waves-light">
                                    Crear
                                </button>
                                <button type="reset" class="btn btn-secondary waves-effect m-l-5">
                                    Cancelar
                                </button>
                            </div>
                        </div>



                </div>     <!-- end card-body --> 
            </div>         <!-- end card --> 
        </div> <!-- end col -->







        <div class="col-lg-6">
            <div class="card">
                <div class="card-body">

                    <h4 class="mt-0 header-title">Datos del canal creado</h4>
                    
                    <small>Nombre del canal</small>
                    <h4>Cachipum</h4>

                    <small>Tamaño player</small>
                    <h4>1280 X 720 px</h4>
                
                <iframe width="100%" height="315" src="https://www.youtube.com/embed/E7oxiG4dNVM" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                
                                                <div class="form-group">
                                                        <label>Código Iframe</label>
                                                        <div>
                                                            <textarea required class="form-control" rows="3"></textarea>
                                                        </div>
                                                    </div>
                                            
                    <div class="form-group">
                            <label>URL Emisión</label>
                            <div class="bootstrap-filestyle input-group"><input type="text" class="form-control " placeholder="" disabled=""> <span class="group-span-filestyle input-group-append" tabindex="0"><label for="filestyle-1" class="btn btn-success "><span class="buttonText">Copiar</span></label></span></div>
                        </div>

                        <div class="form-group">
                            <label>Nombre o clave de la emisión (pega lo siguiente en el codificador)</label>
                            <div class="bootstrap-filestyle input-group"><input type="text" class="form-control " placeholder="" disabled=""> <span class="group-span-filestyle input-group-append" tabindex="0"><label for="filestyle-1" class="btn btn-success "><span class="buttonText">Copiar</span></label></span></div>
                        </div>
                </div>
            </div>
        </div> <!-- end col -->

    </div> <!-- end row -->     
</template>


<script>

import VueSweetalert2 from 'vue-sweetalert2'; 
Vue.use(VueSweetalert2);


export default {
    data() {
        return {
            arrayCanales: [],
            nombre_canal: ''

        }
    },

    methods: {
        // listarCanal() {
        //     axios
        //         .get("/canales_ok")
        //         .then( (response) => {
        //             console.log(response);
        //             this.arrayCanales = response.data.canales;
                
        //         })
        //         .catch(function(error) {
        //             console.log(error);
        //         });
        // },

        crearCanal(){
           axios
                .post("/canales", {
                    nombre_canal: this.nombre_canal,
                    //this.arrayCanales = response.data.canales;

                })
                .then( (response) => {
                     Vue.swal({
                        toast: true,
                        type: 'info',
                        position: 'top-end',
                        showConfirmButton: false,
                        timer: 2000,
                        title: 'creado'
            });
                    
                
                })
                .catch(function(error) {
                    console.log(error);
                });

        }
    },

    mounted() {
     
    }
}



</script>