<template>
    <div id="app" class="form_contenido text-center">
      <div class="container mt-5">
        <h1 class="text-center">PMR INFORMES</h1><br />
        <ul class="nav nav-tabs justify-content-center" id="myTab" role="tablist">
            <li class="nav-item" role="presentation">
                <a class="nav-link active" id="tab1-tab" data-bs-toggle="tab" href="#tab1" role="tab" aria-controls="tab1" aria-selected="true">NARROWCAST</a>
            </li>
            <li class="nav-item" role="presentation">
                <a class="nav-link" id="tab2-tab" data-bs-toggle="tab" href="#tab2" role="tab" aria-controls="tab2" aria-selected="false">LLEGADA</a>
            </li>
            <li class="nav-item" role="presentation">
                <a class="nav-link" id="tab3-tab" data-bs-toggle="tab" href="#tab3" role="tab" aria-controls="tab3" aria-selected="false">SALIDA</a>
            </li>
        </ul>
        <div class="tab-content" id="myTabContent">
            <!-- PESTAÑA NARROWCAST -->
            <div class="tab-pane fade show active" id="tab1" role="tabpanel" aria-labelledby="tab1-tab">
              <br />
                  <div class="form_contenido narrowcast">
                      <div class="subform-header">
                          <h2 class="subform-title">Narrowcast</h2>
                      </div>
                      <form>
                        <div class="row mb-3">
                          <div class="col">
                            <label for="compania" class="form-label">Compañía</label>
                            <input v-model="compania" type="text" class="form-control" id="compania" required>
                          </div>
                          <div class="col">
                            <label for="vuelo" class="form-label">Vuelo</label>
                            <input v-model="vuelo" type="number" class="form-control" id="vuelo" required>
                          </div>
                          <div class="col">
                            <label for="matricula" class="form-label">Matrícula</label>
                            <input v-model="matricula" type="text" class="form-control" id="matricula">
                          </div>
                          <div class="col">
                            <label for="fecha" class="form-label">Fecha</label>
                            <input v-model="fecha" type="date" class="form-control" id="fecha" required>
                          </div>
                        </div>
                        <div class="row mb-3">
                          <div class="col">
                            <label for="hora" class="form-label">Hora estimada</label>
                            <input v-model="hora" type="time" class="form-control" id="hora" required>
                          </div>
                          <div class="col">
                            <label for="codigo" class="form-label">Código</label>
                            <input type="text" class="form-control" id="codigo" value="19" readonly disabled :style="sty_cod">
                          </div>
                          <div class="col">
                            <label for="dly" class="form-label">DLY</label>
                            <input v-model="dly" type="number" class="form-control" id="dly" required>
                          </div>
                          <div class="col">
                            <div class="campo-fantasma">Este es un campo fantasma
                              <input class="form-control" />
                            </div>
                          </div>
                        </div>
                      </form>
                  </div>
                  <div class="form_contenido data">
                      <div class="subform-header">
                          <h2 class="subform-title">Datos asociados</h2>
                      </div>
                      <form>
                        <div class="row mb-3">
                          <div class="col">
                            <label for="vueloLlegada" class="form-label">Vuelo de Llegada</label>
                            <input v-model="vueloLlegada" type="number" class="form-control" id="vueloLlegada" required>
                          </div>
                          <div class="col">
                            <label for="sta" class="form-label">STA</label>
                            <input v-model="sta" type="time" class="form-control" id="sta" required>
                          </div>
                          <div class="col">
                            <label for="eta" class="form-label">ETA</label>
                            <input v-model="eta" type="time" class="form-control" id="eta" required>
                          </div>
                          <div class="col">
                            <label for="ardt" class="form-label">ARDT</label>
                            <input v-model="ardt" type="time" class="form-control" id="ardt" required>
                          </div>
                        </div>
                        <div class="row mb-3">
                          <div class="col">
                            <label for="vueloSalida" class="form-label">Vuelo de Salida</label>
                            <input v-model="vueloSalida" type="number" class="form-control" id="vueloSalida" required>
                          </div>
                          <div class="col">
                            <label for="std" class="form-label">STD</label>
                            <input v-model="std" type="time" class="form-control" id="std" required>
                          </div>
                          <div class="col">
                            <label for="etd" class="form-label">ETD</label>
                            <input v-model="etd" type="time" class="form-control" id="etd" required>
                          </div>
                          <div class="col">
                            <label for="aobt" class="form-label">AOBT</label>
                            <input v-model="aobt" type="time" class="form-control" id="aobt" required>
                          </div>
                        </div>
                      </form>
                  </div>
            </div>
            <!-- PESTAÑA LLEGADA -->
            <div class="tab-pane fade" id="tab2" role="tabpanel" aria-labelledby="tab2-tab">
                  <br />
                  <!-- FORMULARIO DE LLEGADA CON EL FORMATO DE SALIDA -->
                  <div class="form_contenido form_LLG">
                      <div class="subform-header d-flex justify-content-between align-items-center">
                          <h2 class="subform-title">Llegada</h2>
                          <div class="align-self-start mt-2">
                              <label for="noAs_LLG" class="form-label font-weight-extra-bold text-white">¡NO HAY ASISTENCIAS!</label>&nbsp;
                              <input v-model="noAs_LLG" type="checkbox" class="form-check-input" id="noAs_LLG" @change="t_llegada($event.target)">
                          </div>
                      </div>
                      <div class="container">
                          <div class="row">
                              <div class="col-md-6">
                                  <form>
                                    <div class="mb-3">
                                          <label for="ve_llg" class="form-label">VEHÍCULO</label>
                                          <select v-model="ve_llg" :disabled="cMLLG" class="form-select" id="ve_llg" required>
                                              <option value="" disabled selected>Elige una opción</option>
                                              <option value="furgo_op_llg">FURGONETA - 1 OPERARIO</option>
                                              <option value="ambu_op_llg">AMBULIFT - 2 OPERARIOS</option>
                                          </select>
                                      </div>
                                      <div class="mb-3">
                                        <label for="silla_in_llg" class="form-label">SILLA P/E/M (?)</label>
                                        <select id="silla_in_llg" v-model="silla_in_llg" :disabled="cMLLG || ve_llg === 'furgo_op_llg'" class="form-select">
                                          <option value="" selected>NO</option>
                                          <option value="sm_llg">SILLA MANUAL</option>
                                          <option value="se_llg">SILLA ELÉCTRICA</option>
                                          <option value="me_llg">MOTO ELÉCTRICA</option>
                                        </select>
                                      </div>
                                      <div class="mb-3">
                                          <label for="pmrs_llg" class="form-label">PMR'S</label>
                                          <input v-model="pmrs_llg" :disabled="cMLLG" type="text" class="form-control" id="pmrs_llg" required>
                                      </div>
                                      <div class="mb-3">
                                          <label for="parking_LLG" class="form-label">PARKING</label>
                                          <input v-model="parking_LLG" :disabled="cMLLG" type="number" class="form-control" id="parking_LLG" required>
                                      </div>
                                      <hr />
                                      <div class="mb-3" v-if="ve_llg === 'ambu_op_llg'">
                                          <label for="hca_llg" class="form-label">HCA</label>
                                          <input v-model="hca_llg" :disabled="cMLLG" type="time" class="form-control" id="hca_llg" required>
                                      </div>
                                      <div class="mb-3" v-if="ve_llg === 'ambu_op_llg' && (silla_in_llg === 'sm_llg' || silla_in_llg === 'se_llg' || silla_in_llg === 'me_llg')">
                                          <label for="hsb_rem_llg" class="form-label">HSB</label>
                                          <input v-model="hsb_rem_llg" :disabled="cMLLG" type="time" class="form-control" id="hsb_rem_llg" required>
                                      </div>
                                      <div class="mb-3" v-if="ve_llg === 'ambu_op_llg'">
                                          <label for="hda_llg" class="form-label">HDA</label>
                                          <input v-model="hda_llg" :disabled="cMLLG" type="time" class="form-control" id="hda_llg" required>
                                      </div>
                                  </form>
                              </div>
                              <div class="col-md-6">
                                  <form>
                                      <div class="mb-3">
                                          <label for="hpk_llg" class="form-label">HPK</label>
                                          <input v-model="hpk_llg" :disabled="cMLLG" type="time" class="form-control" id="hpk_llg" required>
                                      </div>
                                      <div class="mb-3">
                                          <label for="calzosAvio" class="form-label">CALZOS DE AERONAVE</label>
                                          <input v-model="calzosAvio" :disabled="cMLLG" type="time" class="form-control" id="calzosAvio" required>
                                      </div>
                                      <div class="mb-3">
                                          <label for="aperturaAvio" class="form-label">APERTURA DE AERONAVE</label>
                                          <input v-model="aperturaAvio" :disabled="cMLLG" type="time" class="form-control" id="aperturaAvio" required>
                                      </div>
                                      <div class="mb-3">
                                          <label for="desembarqueAsistencias" class="form-label">DESEMBARQUE</label>
                                          <input v-model="desembarqueAsistencias" :disabled="cMLLG" type="time" class="form-control" id="desembarqueAsistencias" required>
                                      </div>
                                  </form>
                              </div>
                          </div>
                      </div>
                  </div>
              </div>
            <!-- PESTAÑA SALIDA -->
            <div class="tab-pane fade" id="tab3" role="tabpanel" aria-labelledby="tab3-tab">  
              <br />
              <!-- FORMULARIO DE SALIDA -->
                  <div class="form_contenido form_SAL">
                    <div class="subform-header d-flex justify-content-between align-items-center">
                      <h2 class="subform-title">Salida</h2>
                      <div class="align-self-start mt-2">
                        <label for="noAS_SAL" class="form-label font-weight-extra-bold text-white">¡NO HAY ASISTENCIAS!</label>&nbsp;
                        <input v-model="noAs_SAL" type="checkbox" class="form-check-input" id="noAs_SAL" @change="t_salida($event.target)">
                      </div>
                    </div>
                    <div class="container">
                      <div class="row">
                        <div class="col-md-6">
                            <form>
                              <div class="mb-3">
                                  <label for="acc_sal" class="form-label">ACCESO</label>
                                  <select id="acc_sal" v-model="acc_sal" :disabled="cMSAL" class="form-select">
                                    <option value="" disabled selected>Escoge una opción</option>
                                    <option value="finger_sal">FINGER</option>
                                    <option value="remo_sal">REMOTO</option>
                                  </select>
                              </div>
                              <div class="mb-3">
                                  <label for="silla_in_sal" class="form-label">SILLA P/E/M (?)</label>
                                  <select id="silla_in_sal" v-model="silla_in_sal" :disabled="cMSAL" class="form-select">
                                    <option value="" selected>NO</option>
                                    <option value="sm_sal">SILLA MANUAL</option>
                                    <option value="se_sal">SILLA ELÉCTRICA</option>
                                    <option value="me_sal">MOTO ELÉCTRICA</option>
                                </select>
                              </div>
                              <hr />
                              <div class="mb-3" v-if="acc_sal === 'remo_sal'">
                                <label for="ve_sal" class="form-label">VEHÍCULO</label>
                                <select id="ve_sal" v-model="ve_sal" :disabled="cMSAL" class="form-select">
                                  <option value="furgo_op">FURGONETA - 1 OPERARIO</option>
                                  <option value="ambu_op">AMBULIFT - 2 OPERARIOS</option>
                                </select>
                              </div>
                              <div class="mb-3" v-if="acc_sal === 'finger_sal'">
                                <label for="opr_sal" class="form-label">OPERARIOS</label>
                                <input v-model="opr_sal" :disabled="cMSAL" type="number" class="form-control" id="opr_sal" required>
                              </div>
                              <transition name="fade">
                                <div class="mb-3" v-if="acc_sal === 'remo_sal'">
                                  <label for="parking_SAL" class="form-label">PARKING</label>
                                  <input v-model="parking_SAL" :disabled="cMSAL" type="number" class="form-control" id="parking_SAL" required>
                                </div>
                              </transition>
                              <div class="mb-3" v-if="acc_sal === 'remo_sal'">
                                <label for="hpk_sal" class="form-label">HPK</label>
                                <input v-model="hpk_sal" :disabled="cMSAL" type="time" class="form-control" id="hpk_sal" required>
                              </div>
                              <div class="mb-3" v-if="acc_sal === 'remo_sal' && ve_sal === 'ambu_op'">
                                <label for="hca_sal" class="form-label">HCA</label>
                                <input v-model="hca_sal" :disabled="cMSAL" type="time" class="form-control" id="hca_sal" required>
                              </div>
                              <div class="mb-3" v-if="acc_sal === 'remo_sal' && (silla_in_sal === 'sm_sal' || silla_in_sal === 'se_sal' || silla_in_sal === 'me_sal')">
                                <label for="hsb_rem_sal" class="form-label">HSB</label>
                                <input v-model="hsb_rem_sal" :disabled="cMSAL" type="time" class="form-control" id="hsb_rem_sal" required>
                              </div>
                              <div class="mb-3" v-if="acc_sal === 'remo_sal' && ve_sal === 'ambu_op'">
                                <label for="hda_sal" class="form-label">HDA</label>
                                <input v-model="hda_sal" :disabled="cMSAL" type="time" class="form-control" id="hda_sal" required>
                              </div>
                          </form>
                        </div>
                        <div class="col-md-6">
                              <form>
                                <div class="mb-3">
                                  <label for="pmrs_sal" class="form-label">PMR'S</label>
                                  <input v-model="pmrs_sal" :disabled="cMSAL" type="text" class="form-control" id="pmrs_sal" required>
                                </div>
                                <div class="mb-3">
                                  <label for="p_embarque" class="form-label">PUERTA DE EMBARQUE</label>
                                  <input v-model="p_embarque" :disabled="cMSAL" type="text" class="form-control" id="p_embarque" required>
                                </div>
                                <div class="mb-3">
                                  <label for="hllp_sal" class="form-label">HLLP (HORA LLEGADA A PUERTA)</label>
                                  <input v-model="hllp_sal" :disabled="cMSAL" type="time" class="form-control" id="hllp_sal" required>
                                </div>
                                <div class="mb-3">
                                  <label for="hape_sal" class="form-label">APERTURA DE PUERTAS</label>
                                  <input v-model="hape_sal" :disabled="cMSAL" type="time" class="form-control" id="hape_sal" required>
                                </div>
                                <div class="mb-3">
                                  <label for="hpre_sal" class="form-label">HORA PRE-EMBARQUE</label>
                                  <input v-model="hpre_sal" :disabled="cMSAL" type="time" class="form-control" id="hpre_sal" required>
                                </div>
                                <div class="mb-3">
                                  <label for="hem_sal" class="form-label">HORA EMBARQUE</label>
                                  <input v-model="hem_sal" :disabled="cMSAL" type="time" class="form-control" id="hem_sal" required>
                                </div>
                                <div class="mb-3">
                                  <label for="haba_sal" class="form-label">HORA A BORDO ASISTENCIAS</label>
                                  <input v-model="haba_sal" :disabled="cMSAL" type="time" class="form-control" id="haba_sal" required>
                                </div>
                                <div class="mb-3" v-if="silla_in_sal !== '' && acc_sal === 'finger_sal'">
                              <label for="hsb_fin_sal" class="form-label">HORA SILLA EN BODEGA</label>
                              <input v-model="hsb_fin_sal" :disabled="cMSAL" type="time" class="form-control" id="hsb_fin_sal" required>
                            </div>
                          </form>
                    </div>
                  </div>
                </div>    
              </div>
            </div>
        </div>
      </div>
      <div class="row mt-3">
         <div class="col">
            <div class="position-fixed bottom-0 end-0 p-3">
              <button @click="generarPDF" class="btn btn-primary mb-3">Generar PDF</button>
            </div>
            <div class="position-fixed bottom-0 end-0 p-3" style="margin-bottom: 3.5rem;">
              <button @click="limpiarCampos" class="btn btn-secondary">Limpiar Campos</button>
            </div>
          </div>
        </div>
    </div>   
</template>
  
<script>
import jsPDF from "jspdf";
import "jspdf-autotable";
export default {
  methods: {
    calcularEP(STA, STD) {
      const staMinutes = this.convertirHoraAMinutos(STA);
      const stdMinutes = this.convertirHoraAMinutos(STD);
      const diffMinutes = stdMinutes - staMinutes;
      return diffMinutes;
    },
    calcularER(ETA, ETD) {
      const etaMinutes = this.convertirHoraAMinutos(ETA);
      const etdMinutes = this.convertirHoraAMinutos(ETD);
      const diffMinutes = etdMinutes - etaMinutes;
      return diffMinutes;
    },
    convertirHoraAMinutos(hora) {
      const [hours, minutes] = hora.split(":");
      return parseInt(hours) * 60 + parseInt(minutes);
    },
    generarPDF() {
      const pdf = new jsPDF({ orientation: "landscape" });
        // Contenido de la tabla
        const tablaNarrowcast = [
            ["Compañía", "Vuelo", "Matrícula", "Fecha", "Hora estimada", "Código", "DLY"],
            [this.compania, this.vuelo, this.matricula, this.fecha, this.hora, this.codigo, this.dly],
            // ... más filas ...
        ];
        //
        const estilos = {
          tableLineColor: [255, 255, 255],
          tableLineWidth: 0.1,
          headStyles: { fillColor: [255, 0, 0] }, // Estilo del encabezado
          alternateRowStyles: { fillColor: [200, 200, 200] }, // Estilo de filas alternas
          bodyStyles: { textColor: [0, 0, 0], fontSize: 10 }, // Estilo del contenido del cuerpo    
        };
        // Tabla Narrowcast
        pdf.autoTable({
            body: tablaNarrowcast,
            startY: 20,
            styles: estilos,
        });
        // ESCALAS Y DLY
          pdf.setFontSize(8);
          pdf.text("ESCALA PROGRAMADA: " + this.calcularEP(this.sta,this.std) + " MINUTOS",15,50);
          pdf.text("ESCALA REAL: " + this.calcularER(this.eta,this.etd) + " MINUTOS",15,55);
          pdf.text("MINUTOS DLY: " + this.dly,15,60);
          //
          pdf.text("VUELO DE LLEGADA " + this.compania + " " + this.vueloLlegada + " " + "STA: " + this.sta + " " + "ETA: " + this.eta,15,70);
          pdf.text("PARKING: " + this.parking_LLG,15,75);
          if (this.cMLLG) {pdf.text("PMR'S: -",15,80);} else {pdf.text("PMR'S: " + this.pmrs_llg,15,80);}
          if (this.cMLLG) {pdf.text("MEDIOS: -",15,85);} else {pdf.text("MEDIOS: " + this.op_vel_llg[this.ve_llg],15,85);}
          //
          if (this.cMLLG) {pdf.text("NO SE REALIZAN ASISTENCIAS EN ESTE VUELO",15,100);}
          //
          pdf.text("VUELO DE SALIDA " + this.compania + " " + this.vueloSalida + " " + "STD: " + this.std + " " + "ETD: " + this.etd,15,115);
          pdf.text("PUERTA DE EMBARQUE: " + this.p_embarque,15,120);
          if (this.acc_sal === "remo_sal") {pdf.text("PARKING: " + this.parking_SAL,15,125);} else {pdf.text("PARKING: -",15,125);}
          if (this.cMSAL) {pdf.text("PMR'S: -",15,130);} else {pdf.text("PMR'S: " + this.pmrs_sal,15,130);}
          if (this.cMSAL) {pdf.text("MEDIOS: -",15,135);} 
            else if (this.acc_sal === "remo_sal") {
              pdf.text("MEDIOS: " + this.op_vel_sal[this.ve_sal],15,135);}
            else if (this.acc_sal === "finger_sal") {
              pdf.text("MEDIOS: " + this.opr_sal + " OPERARIOS",15,135);}
          
          //
          if (this.cMSAL) {pdf.text("NO SE REALIZAN ASISTENCIAS EN ESTE VUELO",15,155);}

          //
          if (this.cMLLG && this.cMSAL) {
            pdf.text("Entendemos que no es un retraso imputable a PMR ya que para el vuelo asociado de llegada no se realizan asistencias; y para el vuelo asociado de salida tampoco se realizan asistencias.",15,175);
            pdf.text("Reciban un cordial saludo.",15,185)
          }
          
      
        
      pdf.save("formulario.pdf");
    },
    //
    t_llegada(checkbox) {
      const formulario = checkbox.closest(".form_LLG");
      const campos = formulario.querySelectorAll(".campo input, .campo select");
      for (let i = 0; i < campos.length; i++) {
        if (campos[i] !== checkbox) {
          // Evitar deshabilitar el propio checkbox
          campos[i].disabled = checkbox.checked;
        }
      }
      this.cMLLG = checkbox.checked;
    },
    //
    t_salida(checkbox) {
      const formulario = checkbox.closest(".form_SAL");
      const campos = formulario.querySelectorAll(".campo input, .campo select");
      for (let i = 0; i < campos.length; i++) {
        if (campos[i] !== checkbox) {
          // Evitar deshabilitar el propio checkbox
          campos[i].disabled = checkbox.checked;
        }
      }
      this.cMSAL = checkbox.checked;
    },
    //
  },
  data() {
    return {
      compania: "",
      vuelo: "",
      fecha: "",
      hora: "",
      codigo: "19",
      matricula: "",
      dly: "",
      sta: "", // Inicializa con el valor adecuado
      std: "", // Inicializa con el valor adecuado
      eta: "", // Inicializa con el valor adecuado
      etd: "",
      noAs_LLG: false,
      noAs_SAL: false,
      parkingLLG: "",
      hsb_rem_llg: "",
      hsb_fin_sal: "",
      pmrs_llg: "",
      pmrs_sal: "",
      ve_llg: "",
      hpk_sal: "",
      hpk_llg: "",
      calzosAvio: "",
      hca_llg: "",
      hca_sal: "",
      hda_llg: "",
      hda_sal: "",
      parking_LLG: "",
      aperturaAvio: "",
      desembarqueAsistencias: "",
      hda: "",
      acc_sal: "",
      silla_in_sal: "",
      silla_in_llg: "",   
      data_ni: "",
      ve_sal: "",
      hpre_sal: "",
      hem_sal: "",
      cMLLG: false,
      cMSAL: false,
      sty_cod: {
      'background-color': '#00A135',
      'color': '#ffffff',
      'font-weight': 'bold',
      },
      op_vel_llg: {
          furgo_op_llg: "FURGONETA - 1 OPERARIO",
          ambu_op_llg: "AMBULIFT - 2 OPERARIOS"
      },
      op_vel_sal: {
        furgo_op: "FURGONETA - 1 OPERARIO",
        ambu_op: "AMBULIFT - 2 OPERARIOS"
      },
    };
  },
};
</script>
<style scoped>
/* Estilos para los subformularios */
.narrowcast,
.data,
.form_LLG, .form_SAL {
  background-color: #f9f9f9;
  border-radius: 10px;
  padding: 20px;
  margin-bottom: 20px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
 }

.form_LLG, .form_SAL {
  background-color: #fff;
  border: 1px solid #ccc;
  padding: 15px;
}

/* Estilos para los campos */
.campo label {
  font-weight: bold;
}

/* Estilos para los botones */
.btn-primary {
  background-color: #007bff;
  border-color: #007bff;
}

.btn-primary:hover {
  background-color: #0056b3;
  border-color: #0056b3;
}
.subform-header {
  background-color: #094293;
  color: #f9f9f9;
  padding: 10px;
  border-radius: 5px;
  margin-bottom: 20px;
}

.subform-title {
  margin: 0;
}
.form_contenido form .mb-3 label {
  text-align: left;
  display: block;
  font-weight: bold;
}
.form-control[disabled], select[disabled] {
  background-color: #fa768c;
  cursor: not-allowed;
}
.form-label{
  font-weight: bold;
}
/* Estilos para el checkbox */
.custom-checkbox {
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  width: 24px;
  height: 24px;
  background-color: white;
  border: 2px solid #ccc;
  border-radius: 4px;
  vertical-align: middle;
  position: relative;
}

.custom-checkbox:checked {
  background-color: #007bff;
  border-color: #007bff;
}

.custom-checkbox:checked::before {
  content: '\2713'; /* Símbolo de check */
  color: white;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 16px;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
  opacity: 0;
}
.campo-fantasma {
  visibility: hidden; /* Oculta el contenido */
  position: absolute; /* Elimina el campo del flujo normal */
}
</style>