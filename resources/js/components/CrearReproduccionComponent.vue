<template>

<div class="page-title-box">
    <div class="row align-items-center">
        <div class="col-sm-7 bread">
            <h4 class="page-title">Crear Playlist</h4>
            <ol class="breadcrumb">
              <li class="breadcrumb-item"><a href="javascript:void(0);">Dashboard</a></li>
              <li class="breadcrumb-item active">Crear Playlist</li>
            </ol>
          </div>
        </div>

  <div class="row">

                    <div class="col-xl-12">
                        <div class="card">
                            <div class="card-body">
                                <div class="row">
                                    
 <div class="col-lg-8">
                <form class action="#">
                  <div class="form-group row">
                    <label for="example-text-input" class="col-sm-4 col-form-label">Nombre</label>
                    <div class="col-8">
       
                      <input class="form-control" type="text" v-model="nombre_playlist" placeholder="Lista de Reproducción" id="example-text-input"/>
            
           
                    </div>
                  </div>

                  <div class="form-group row">
                    <label for="example-text-input" class="col-sm-4 col-form-label">Usuario</label>
                    <div class="col-8">
                      <div class="form-group">
                        <select class="form-control" v-model="id_usuario">
                          <option value="0" disabled>Seleccione</option>
                          <option v-for="usuarios in arrayUsers" :key="usuarios.id" :value="usuarios.id" v-text="usuarios.nombre_usuario"
                          ></option>
                        </select>
                      </div>
                    </div>
                  </div>

                  <div class="form-group row">
                    <label for="example-text-input" class="col-sm-4 col-form-label">Canal</label>
                    <div class="col-8">
                      <select class="form-control" v-model="id_canal">
                        <option value="0" disabled>Seleccione</option>
                        <option v-for="canales in arrayCanales" :key="canales.id" :value="canales.id" v-text="canales.nombre_canal"
                        ></option>
                      </select>
                    </div>
                  </div>

                  <div class="form-group row">
                    <label for="example-time-input" class="col-sm-4 col-form-label">Hora Inicio</label>
                    <div class="col-8">
                      <input class="form-control" type="time" step="1" value="13:45:00" v-model= "hora_inicio" id="example-time-input" />
                    </div>
                  </div>

                  <div class="form-group row">
                    <label for="example-date-input" class="col-sm-4 col-form-label">Emisión</label>
                    <div class="col-8">
                      <input class="form-control" type="date" value="2011-08-19" id="example-date-input" v-model="fecha_emision"/>
                    </div>
                  </div>

                  <div class="form-group row ">
                    <label for="example-time-input" class="col-form-label">Loop</label>

                    <input type="checkbox" id="switch7" switch="info" checked />
                    <label class="loop" for="switch7" data-on-label="Si" data-off-label="No"></label>

                    <label for="example-time-input" class="col-form-label">AutoStart</label>

                    <input type="checkbox" id="switch8" switch="info" checked />
                    <label class="loop" for="switch8" data-on-label="Si" data-off-label="No"></label>

                    <!--<button type="submit" class="btn btn-primary waves-effect waves-light mr-1">Crear</button>-->
                  </div>
                  
                </form>
              </div>


                  <div class="col-lg-4">
                      <div class="row">
                            <div id="gzplayer"></div>
                      </div>
                  </div>
                </div>
                <!-- end row -->
            </div>
        </div>
        <!-- end card -->
    </div>




    <!-- modal inicio -->
      <div v-if="showModal">
        <transition name="fade1">
          <div class="modal fade1-enter-active bs-example-modal-center show" tabindex="-1" role="dialog" aria-labelledby="mySmallModalLabel" style="display: block; padding-right: 17px;" aria-modal="true">
            <div class="modal-dialog modal-dialog-centered">
              <div class="modal-content">
                <div class="modal-header">
                  <h5 class="modal-title mt-0">Agregar Evento Live</h5>
                  <button type="button" class="close" data-dismiss="modal" aria-hidden="true" @click="showModal = false">×</button>
                </div>
                <div class="modal-body">
                  <label for="example-time-input" class="col-form-label">Nombre live</label>
                  <input class="form-control" type="text" step="1" value="13:45:00" v-model="nombre_live" />
                  <label for="example-time-input" class="col-form-label">Duración live</label>
                  <input class="form-control" type="time" step="1" v-model="duration_live" /><br><br>
                   <button type="button" class="btn btn-success" @click="agregarLiveVideo()">
                    <i class="ion ion-md-add-circle"></i> Agregar
                  </button>
                </div>
              </div>
            </div>
          </div>
        </transition>
      </div> 
    <!-- modal fin -->



    <div class="col-lg-4">
      <div class="card">
        <div class="card-body">
          
            <button type="button" class="btn btn-success" @click="showModal = true">
              <i class="ion ion-md-add-circle"></i> Live
            </button>
             

            <!-- <button type="submit" class="btn btn-primary dropdown-toggle">Categorias</button> -->
            
        
<div class="btn-group m-b-10">
  <button type="button" class="btn btn-primary">Primary</button>
   <button type="button" class="btn btn-primary dropdown-toggle dropdown-toggle-split" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false"><span class="sr-only">Toggle Dropdown</span></button>
   <div class="dropdown-menu" x-placement="bottom-start" style="position: absolute; will-change: transform; top: 0px; left: 0px; transform: translate3d(73px, 35px, 0px);">
     <a class="dropdown-item" href="#">Action</a> 
     <a class="dropdown-item" href="#">Another action</a> 
     <a class="dropdown-item" href="#">Something else here</a>
     <div class="dropdown-divider"></div>
     <a class="dropdown-item" href="#">Separated link</a>
  </div>
</div>

            </br>
            <label> <input type="videos" v-model="busqueda" class="form-control form-control-sm" placeholder="Buscar Vídeos" aria-controls="DataTables_Table_0"></label>




          
          <div class="table-wrapper-scroll-y my-custom-scrollbar">
          <table class="table table-sm m-0">
            <thead>
              <tr>
                <th>Nombre Video</th>
                <th>Tiempo</th>
                 <!--<th>Peso</th>-->
                <th><center>Agregar</center></th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="videos in buscarPorTitulo" :key="videos.id">
                <td v-text="videos.nombre_video"></td>
                <td v-text="parseToHour(videos.lenght)"></td>
                <td v-text="convertirBytes(videos.size)"></td>
                <td>
                  <button
                    @click="agregarDetalleVideo(videos)"
                    class="btn btn-success btn-sm form-control btnagregar"
                  >
                    <i class="ti-plus"></i>
                  </button>
                </td>
              </tr>
            </tbody>
          </table>
          </div>
        </div>
      </div>
    </div>

    
    <div class="col-lg-8">
      <div class="card">
        <div class="card-body">
          <div class="table-striped">
            <table class="table table-sm m-10 table-striped">
              <thead>
                <tr>
                  <th>Entrada</th>
                  <th>Salida</th>
                  <th>Nombre Video</th>
                  <th>Duración</th>
                  <th><center>Eliminar</center></th>
                </tr>
              </thead>
              <draggable
                v-model="arrayDetallePlaylist"
                v-bind="dragOptions"
                @start="drag = true"
                @end="drag = false"
                tag="tbody"
              >
                <!-- <tr :class="[classEsActiva ? 'table-success' : 'table-info']" v-for="(videoDetalle,index) in itemsWithSubTotal" :key="index"> -->
                <tr :class="[(videoDetalle.item1.live=='live') ? 'bg-secondary' : '' ]" v-for="(videoDetalle,index) in itemsWithSubTotal" :key="index"> 
                  <td>{{ parseToHour(videoDetalle.subinit) }}</td>
                  <td>{{ parseToHour(videoDetalle.subtotal) }}</td>
                  <td>{{ videoDetalle.item1.nombre_video }}</td>
                  <td>{{ parseToHour(videoDetalle.item1.testduration) }}</td>
                  <td><center>
                    <button
                      type="submit"
                      class="btn btn-danger waves-effect waves-light mx-auto"
                      @click="eliminarDetalleVideo(index)"
                    ><i class="ti-close"></i></button></center>
                  </td>
                </tr>
              </draggable>

              <tfoot>
                <tr>
                  <td></td>
                  <td></td>
                  <td></td>
                  <td></td>
                  <td>
                    <i class="ion ion-md-clock"></i>
                    {{ totalParcial = parseToHour(total()) }}
                  </td>
                  <td></td>
                </tr>
              </tfoot>
            </table>
          </div>

          <button type="submit" class="btn btn-primary waves-effect waves-light mr-1" @click="registrarPlaylist()"><i class="ti-save"></i> Guardar Lista</button>
          <button type="submit" class="btn btn-warning waves-effect waves-light mr-1" @click="onPreview()">
            <i class="ti-control-play"></i> Preview
          </button>
        </div>
      </div>
  
    </div>

    
  </div>
</div>


</template>

<script>





import draggable from "vuedraggable";
var moment = require('moment');

import VueSweetalert2 from 'vue-sweetalert2';
Vue.use(VueSweetalert2);

import { uuid } from 'vue-uuid' // Import uuid

const message = [
  "vue.draggable",
  "draggable",
  "component",
  "for",
  "vue.js 2.0",
  "based",
  "on",
  "Sortablejs"
];
export default {
  name: "transition-example-2",
  display: "Transitions",
  order: 7,
  data() {
    return {
      playlist_id: 0,
      id_video: 0,
      id_usuario: 0,
      id_canal: 0,
      nombre_video: "",
      lenght: 0,
      testduration: 0,
      testinit: 0,
      usuario_id: 0,
      hora_inicio: 0,
      nombre_playlist: "",
      fecha_emision: 0,
      loop: 0,
      auto_start: 0,
      arrayPlaylist: [],
      arrayDetallePlaylist: [],
      arrayCanales: [],
      arrayUsers: [],
      arrayVideo: [],
      arrayTotal: [],
      busqueda: '',
      playlist: [
        {
          "file" : "/uploads/y2.mp4",

        },
         {
          "file" : "/uploads/y2.mp4",

        }
      ],
      now: new Date,
      utc: new Date,
      showModal: false,
      totalParcial: 0,
      nombre_live: '',
      duration_live: 0,
      classEsActiva: false,
      list: message.map((name, index) => {
        return { name, order: index + 1 };
      }),
      drag: false,
      itemsx: [],
      subTotalAcum: 0,
      subInitAcum: 0
    };
  },
  components: {
    draggable
  },
  methods: {
    listarVideo() {
      let esto = this;
      var url = "/videos/listarVideos";
      axios
        .get(url)
        .then(function(response) {
          let respuesta = response.data;
          esto.arrayVideo = respuesta.videos;
          console.log("respuesta total" + response);
        })
        .catch(function(error) {
          console.log(error);
        });
    },

    registrarPlaylist(data) {
      let esto = this  
      axios.post("/playlist/registrar", {
          id_usuario: esto.id_usuario,
          id_canal: esto.id_canal,
          nombre_playlist: esto.nombre_playlist,
          hora_inicio: moment(esto.hora_inicio, 'HH:mm:ss: A').diff(moment().startOf('day'), 'seconds'),
          hora_final: esto.totalParcial,
          fecha_emision: esto.fecha_emision,
          loop: esto.loop,
          auto_start: esto.auto_start,
          data: esto.arrayDetallePlaylist,

     // ID_VIDEO, NOMBRE_VIDEO, TESTDURATION,
          
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
    // AGREGA VIDEOS
    agregarDetalleVideo(data = []) {
      this.classEsActiva = false
      this.arrayDetallePlaylist.push({
        id_video: data["id"],
        nombre_video: data["nombre_video"],
    // convierte la hora de video de entrada a segundos
        testduration: data["lenght"],
      });
    },
    // AGREGA LIVE
     agregarLiveVideo() {
      var v1 = uuid.v1();
        this.classEsActiva = true,
        this.arrayDetallePlaylist.unshift({
        id_video      : v1,
        nombre_video  : this.nombre_live,
        testduration  : moment(this.duration_live, 'HH:mm:ss: A').diff(moment().startOf('day'), 'seconds'),
        live          : 'live'
        
      });
        console.log(testduration);
    },
    eliminarDetalleVideo(index) {
      let esto = this;
      esto.arrayDetallePlaylist.splice(index, 1);
    },
    selectUsuarios() {
      let esto = this;
      var url = "/usuarios/selectUsuarios";
      axios.get(url).then(function(response) {
         
          let respuesta = response.data;
          esto.arrayUsers = respuesta.usuarios;
           console.log(esto.arrayUsers);
        })
        .catch(function(error) {
          console.log(error);
        });
    },
    selectCanales() {
      let esto = this;
      var url = "/canales/selectCanales";
      axios
        .get(url)
        .then(function(response) {
          console.log(response);
          let respuesta = response.data;
          esto.arrayCanales = respuesta.canales;
        })
        .catch(function(error) {
          console.log(error);
        });
    },
    getCanales(val1) {
      let me = this;
      me.loading = true;
      me.id_canal = val1.id;
    },
    sort() {
      this.list = this.list.sort((a, b) => a.order - b.order);
    },
    onPreview(){

      var videos = this.arrayDetallePlaylist;

  //    var playlist = videos.map(({nombre_video}) => ({file :  "http://10.255.255.35/shared-wow/" + nombre_video}))

      var playlist = videos.map(({nombre_video}) => ({file :  "/uploads/" + nombre_video}))

      console.log(playlist);

        // buscar la sintaxis correcta error en el foreach (foreach si not a function)
     
            jwplayer("gzplayer").setup({
              
               "playlist" : playlist
                
            })
      },

    
    computeSubTotal: function(item) {
      //formatPrice is removed here because its not defined in the questions
      this.subTotalAcum = this.subTotalAcum + item.testduration;
      return this.subTotalAcum;
    },

    parseToHour(seconds){
      return moment().startOf('day').seconds(seconds).format('H:mm:ss');
    },
    horaActual(){
      var moment = moment().format('MMMM Do YYYY, h:mm:ss a');
    },
    
    convertirBytes(num) {
            // jacked from: https://github.com/sindresorhus/pretty-bytes
            if (typeof num !== 'number' || isNaN(num)) {
                throw new TypeError('Expected a number');
            }

            var exponent;
            var unit;
            var neg = num < 0;
            var units = ['B', 'kB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'];

            if (neg) {
                num = -num;
            }

            if (num < 1) {
                return (neg ? '-' : '') + num + ' B';
            }

            exponent = Math.min(Math.floor(Math.log(num) / Math.log(1000)), units.length - 1);
            num = (num / Math.pow(1000, exponent)).toFixed(2) * 1;
            unit = units[exponent];

            return (neg ? '-' : '') + num + ' ' + unit;
        },


    total(){
      return this.subTotalAcum
    },


  },

  computed: {
    calcularParcialLengthVideo: function() {
      var resultado = 0;
      for (var i = 0; i < this.arrayDetallePlaylist.length; i++) {
        resultado = resultado + parseInt(this.arrayDetallePlaylist[i].lenght);
      }
      return resultado;
    },
    buscarPorTitulo() { 
      return this.arrayVideo.filter((busqueda) => busqueda.nombre_video.toUpperCase().includes(this.busqueda.toUpperCase()))
    },

    itemsWithSubTotal() {
      //var itemsx = [];
      
      //  console.log(this.hora_inicio); 
      //  console.log(moment(this.hora_inicio, 'HH:mm:ss: A').diff(moment().startOf('day'), 'seconds'));
      
      this.subTotalAcum = moment(this.hora_inicio, 'HH:mm:ss: A').diff(moment().startOf('day'), 'seconds')

      //this.subTotalAcum = moment(this.hora_inicio, 'HH:mm:ss A').diff(moment().startOf('day'), 'seconds');
      //this.subTotalAcum=this.hora_inicio;
      //console.log(this.arrayDetallePlaylist)
      //itemsx = this.arrayDetallePlaylist.map(item1 => ({item1,subtotal: this.computeSubTotal(item1),subinit: this.computeInit(item1)}))
      //this.arrayDetallePlaylist.testinit = 22;
      //console.log(itemsx)
      return this.arrayDetallePlaylist.map(item1 => ({
        
        item1,
        subinit: this.subTotalAcum,
        subtotal: this.computeSubTotal(item1)
        
      }));

    },

    dragOptions() {
      return {
        animation: 200,
        group: "description",
        disabled: false,
        ghostClass: "ghost"
      };
    }
  },

  mounted() {
    this.listarVideo();
    this.selectUsuarios();
    this.selectCanales();


      // this.utc = moment.utc().format('YYYY-MM-DD HH:mm:ss')
      // this.local = moment.utc().local().format('YYYY-MM-DD HH:mm:ss')
    
    

  }
  // created() {
  //   setInterval(() => { 
  //     this.utc = moment.utc().format('YYYY-MM-DD HH:mm:ss')
  //     this.local = moment.utc().local().format('YYYY-MM-DD HH:mm:ss')
    
    
  //   }); 
  // }
};
</script>
 <style >
        .fade1-enter-active, .fade1-leave-active {
        transition: opacity 5s;
        }
        .fade1-enter, .fade1-leave-to /* .fade-leave-active below version 2.1.8 */ {
        opacity: 0;
        }
        .bg-secondary{
          background-color: rgb(62, 119, 68) !important;
        }
    </style>

