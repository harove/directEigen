<template>                   
                    <div class="page-title-box">
                        <div class="row align-items-center">
                           <div class="col-sm-6">
                                <h4 class="page-title">Crear Canal</h4>
                                <ol class="breadcrumb">
                                    <li class="breadcrumb-item"><a href="javascript:void(0);">Dashboard</a></li>
                                    <li class="breadcrumb-item"><a href="javascript:void(0);">Canales</a></li>
                                    <li class="breadcrumb-item active">Crear Canal</li>
                                </ol>
                            </div>
                            
                            </div>
                        
                        <div class="row">
                            <div class="col-lg-12">
                                <div class="card">
                                    <div class="card-body">
        
                                        <h4 class="mt-0 header-title">Crear Canal</h4>
                                        <p class="text-muted m-b-30 ">Parsley is a javascript form validation
                                            library. It helps you provide your users with feedback on their form
                                            submission before sending it to your server.</p>
        

                                                <div class="row">
                                                        <div class="col-md-6">
                                                            <div class="form-group">
                                                                <label>Nombre del Canal</label>
                                                                <input type="text" v-model="nombre_canal" class="form-control" required placeholder="Ingresar nombre del canal"/>
                                                            </div>

                                            
                                                            <div class="form-group">
                                                                    <label>Logo Player <i>(Formatos .jpg .png )</i></label>
                                                            
                                                                    <input type="file" class="filestyle" @change="subirLogo" data-buttonname="btn-secondary" id="filestyle-0" tabindex="-1" style="position: absolute; clip: rect(0px, 0px, 0px, 0px);">

                                                                    <div class="bootstrap-filestyle input-group">
                                                                        <input type="text" class="form-control " placeholder="" disabled=""> 
                                                                        <span class="group-span-filestyle input-group-append" tabindex="0">
                                                                            <label for="filestyle-0" class="btn btn-secondary ">
                                                                                <span class="icon-span-filestyle fas fa-folder-open"></span> 
                                                                                <span class="buttonText">Choose file</span>
                                                                            </label>
                                                                        </span>
                                                                    </div>

                                                                    <img class="img-thumbnail" alt="150x150" width="150" :src="logofile" data-holder-rendered="true">





                                                            </div>

                                                            <div class="form-group">
                                                                <label>Posición de Logo</label><br>
                                                                <div class="custom-control custom-radio custom-control-inline">
                                                                    <input type="radio" @click="changePositionVue('top-left')" id="customRadioInline1" name="customRadioInline1" class="custom-control-input">
                                                                    <label class="custom-control-label" for="customRadioInline1">Toggle this custom radio</label>
                                                                </div>
                                                                <div class="custom-control custom-radio custom-control-inline">
                                                                    <input type="radio" @click="changePositionVue('top-right')" id="customRadioInline2" name="customRadioInline1" class="custom-control-input">
                                                                    <label class="custom-control-label" for="customRadioInline2">Or toggle this other custom radio</label>
                                                                </div>
                                                            </div>
                                                            
                                                             <div class="form-group">
                                                                <label>Logo Link <i>(Formatos .jpg .png )</i></label>
                                                                <input class="form-control" type="url" value="https://ejemplo.cl" id="example-url-input">
                                                            </div>
                                                        </div>
                                            
                                                        <div class="col-md-6">
                                                            <div id="gzplayer"></div>
                                                        </div>
                                            </div>

                                            <div class="form-group">
                                                <div>
                                                    <button type="submit" @click="registrarCanal()" class="btn btn-primary waves-effect waves-light">
                                                        Crear
                                                    </button>
                                                    <button >
                                                        Cancelar
                                                    </button>
                                                </div>
                                            </div>
                                     
        
                                    </div>
                                </div>
                            </div> <!-- end col -->                            
                        </div> <!-- end row --> 
                    </div>
</template>


<script>


import VueSweetalert2 from 'vue-sweetalert2';
Vue.use(VueSweetalert2);
require( 'jwplayer-node' );



export default {
     data() {
        return {
            logofile: '',
            nombre_canal: '',
            tamaño_player: 0,
            imagen_canal: '',
            fondo_canal: ''
        }
    },
    methods: {

       
        registrarCanal(data) {
            axios.post("/canales/registrar", {
                imagen_canal    : esto.imagen_canal,
                nombre_canal    : esto.nombre_canal,
                tamaño_player   : esto.tamaño_player,
                fondo_canal     : esto.fondo_canal
            })
            .then(function(response) {
                Vue.swal({
                        toast: true,
                        type: 'success',
                        position: 'top-end',
                        showConfirmButton: false,
                        timer: 2000,
                        title: 'Ingresado Exitosamente'
                    });
            })
            .catch(function(error) {
                console.log(error);
            });
        },
        subirLogo(e){      
                let file = e.target.files[0];   //files[0] object   first file
                let reader = new FileReader();   
                reader.readAsDataURL(file);
                reader.onload = event => {
                    this.logofile = reader.result;
                } 
        },

            subirFondo(e){
                
                let esto=this;
                let file = e.target.files[0];    //file object
             
                let reader = new FileReader();
                reader.onloadend = (file) => {
                    
                    //console.log('RESULT', reader.result)

                    esto.fondo_canal = reader.result;
                }
                reader.readAsDataURL(file);
            },

             changePositionVue(position) {
                    
                    jwplayer("gzplayer").setup({
                        file: "/uploads/video_1_2M.mp4",
                        logo: {
                            file: this.logofile,
                            position: position,
                            //hide: "true",
                            //autostart: true,
                        }
                    })
                    .load();
                
                },




    }

}
</script>

