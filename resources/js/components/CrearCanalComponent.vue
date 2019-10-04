<template>
    
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
                                                                <label class="control-label">Selección tamaño de player</label>
                                                                <select class="form-control select2" v-model="tamaño_player">
                                                                    <option>Seleccionar</option>
                                                                    <optgroup label="Selección en pixeles">
                                                                        <option value="1">512 x 288</option>
                                                                        <option value="2">640 x 360</option>
                                                                        <option value="3">768 x 432</option>
                                                                        <option value="4">960 x 540</option>
                                                                        <option value="5">1280 x 720</option>
                                                                        <option value="6">1920 x 1080</option>
                                                                    </optgroup>
                                                                </select>
                                                            </div>


                                                        </div>
                                            
                                                        <div class="col-md-4">
                                                            <div class="form-group">
                                                                    <label>Subir Logo del Player</label>
                                                                    <input type="file" @change="subirLogo" class="filestyle" data-buttonname="btn-secondary">
                                                                    <img :src="imagen_canal" class="img-responsive" width="100px" height="100px"> 
                                                            </div>
                                                            <div class="form-group">
                                                                    <label>Subir fondo del Player</label>
                                                                    <input type="file" @change="subirFondo"  class="filestyle" data-buttonname="btn-secondary">
                                                                    <img :src="fondo_canal" class="img-responsive" width="100px" height="100px"> 
                                                            </div>
                                                            
                                                        </div>
                                            </div>

                                            <div class="form-group">
                                                <div>
                                                    <button type="submit" @click="registrarCanal()" class="btn btn-primary waves-effect waves-light">
                                                        Crear
                                                    </button>
                                                    <button type="reset" class="btn btn-secondary waves-effect m-l-5">
                                                        Cancelar
                                                    </button>
                                                </div>
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
            nombre_canal: '',
            tamaño_player: 0,
            imagen_canal: '',
            fondo_canal: ''
        }
    },
    methods: {
        registrarCanal(data) {
            let esto = this;
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
                
                let esto=this;
                let file = e.target.files[0];
             
                console.log(file);

                let reader = new FileReader();

                reader.onloadend = (file) => {
                    
                    //console.log('RESULT', reader.result)

                    esto.imagen_canal = reader.result;
                }
                reader.readAsDataURL(file);
            },
            subirFondo(e){
                
                let esto=this;
                let file = e.target.files[0];
             
                console.log(file);

                let reader = new FileReader();
                reader.onloadend = (file) => {
                    
                    //console.log('RESULT', reader.result)

                    esto.fondo_canal = reader.result;
                }
                reader.readAsDataURL(file);
            },
    }

}
</script>

