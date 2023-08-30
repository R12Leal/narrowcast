<template>
    <div id="app" class="form_contenido text-center">
    <div class="row justify-content-center">
      <div class="col-md-6">
        <div class="narrowcast">
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
                  <input type="text" class="form-control" id="codigo" value="19" readonly>
                </div>
                <div class="col">
                  <label for="dly" class="form-label">DLY</label>
                  <input v-model="dly" type="number" class="form-control" id="dly" required>
                </div>
              </div>
            </form>
          </div>
        </div>
        <div class="row justify-content-center">
        <div class="col-md-6">
        <div class="form_contenido data">
            <div class="subform-header">
                <h2 class="subform-title">Datos asociados</h2>
            </div>
            <form>
              <div class="row mb-3">
                <div class="col">
                  <label for="vueloLlegada" class="form-label">Vuelo asociado de Llegada</label>
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
              </div>
              <div class="row mb-3">
                <div class="col">
                  <label for="vueloSalida" class="form-label">Vuelo asociado de Salida</label>
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
              </div>
            </form>
          </div>
        </div>
        </div>
        <div class="row justify-content-center">
        <div class="col-md-6">
        <div class="form_contenido form_LLG">
            <div class="subform-header">
                <h2 class="subform-title">Llegada</h2>
            </div>
            <form>
              <div class="row mb-3">
                <div class="col">
                  <label for="noAsistencias_llegadas" class="d-flex align-items-center">¡NO HAY ASISTENCIAS!</label>
                  <input v-model="noAsistenciasLlegadas" type="checkbox" class="custom-checkbox mr-2" id="noAsistencias_llegadas" @change="t_llegada($event.target)">
                </div>
                <div class="col">
                  <label for="parking_LLG" class="form-label">Parking</label>
                  <input v-model="parking_LLG" :disabled="checkboxMarcado" type="number" class="form-control" id="parking_LLG" required>
                </div>
                <div class="col">
                  <label for="pmrs" class="form-label">PMR's</label>
                  <input v-model="pmrs" :disabled="checkboxMarcado" type="text" class="form-control" id="pmrs" required>
                </div>
              </div>
              <div class="row mb-3">
                <div class="col">
                  <label for="medios" class="form-label">Medios</label>
                  <select v-model="medios" :disabled="checkboxMarcado" class="form-select" id="medios" @change="t_llegada_medios($event.target)" required>
                    <option value="" disabled selected>Elige una opción</option>
                    <option value="FURGONETA - 1 OPERARIO">FURGONETA - 1 OPERARIO</option>
                    <option value="AMBULIFT - 2 OPERARIOS">AMBULIFT - 2 OPERARIOS</option>
                  </select>
                </div>
                <div class="col">
                  <label for="hpk" class="form-label">HPK</label>
                  <input v-model="hpk" :disabled="checkboxMarcado" type="time" class="form-control" id="hpk" required>
                </div>
                <div class="col">
                  <label for="calzosAvio" class="form-label">Calzos de aeronave</label>
                  <input v-model="calzosAvio" :disabled="checkboxMarcado" type="time" class="form-control" id="calzosAvio" required>
                </div>
              </div>
              <div class="row mb-3">
                <div class="col">
                  <label for="hca" class="form-label">HCA</label>
                  <input v-model="hca" :disabled="checkboxMarcado || medios === 'FURGONETA - 1 OPERARIO'" type="time" class="form-control" id="hca" required>
                </div>
                <div class="col">
                  <label for="aperturaAvio" class="form-label">Apertura de aeronave</label>
                  <input v-model="aperturaAvio" :disabled="checkboxMarcado" type="time" class="form-control" id="aperturaAvio" required>
                </div>
                <div class="col">
                    <label for="desembarqueAsistencias" class="form-label">Desembarque</label>
                <input v-model="desembarqueAsistencias" :disabled="checkboxMarcado" type="time" class="form-control" id="desembarqueAsistencias" required>
              </div>
              <div class="col">
                <label for="hda" class="form-label">HDA</label>
                <input v-model="hda" :disabled="checkboxMarcado || medios === 'FURGONETA - 1 OPERARIO'" type="time" class="form-control" id="hda" required>
              </div>
            </div>
          </form>
        </div>
        </div>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col">
        <button @click="generarPDF" class="btn btn-primary position-fixed bottom-0 end-0 m-3">Generar PDF</button>
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
      const estilos = {
        tableLineColor: [0, 0, 0], // Color de los bordes de la tabla (negro en este caso)
        alternateRowStyles: { fillColor: [240, 240, 240] }, // Color de fila alternada (gris claro en este caso)
        };
        // Contenido de la tabla
        const tablaNarrowcast = [
            ["Compañía", "Vuelo", "Fecha", "Hora estimada", "Código", "DLY"],
            [this.compania, this.vuelo, this.fecha, this.hora, this.codigo, this.dly],
            // ... más filas ...
        ];
        // Tabla Narrowcast
        pdf.autoTable({
                headStyles: { fillColor: [111, 168, 220] },
                body: tablaNarrowcast,
                startY: 20,
                styles: estilos,
        });
        // ESCALAS Y DLY
          pdf.setFontSize(8);
          pdf.text("ESCALA PROGRAMADA: " + this.calcularEP(this.sta,this.std) + " MINUTOS",15,50);
          pdf.text("ESCALA REAL: " + this.calcularER(this.eta,this.etd) + " MINUTOS",15,55);
          pdf.text("MINUTOS DLY: " + this.dly,15,60);
          pdf.text("VUELO DE LLEGADA " + this.compania + " " + this.vuelo + " " + "STA: " + this.sta + " " + "ETA: " + this.eta,15,70);
          pdf.text("PARKING: " + this.parkingLLG,15,75);
          
        // CONDICIONAL PARA COMPROBAR EN LLEGADAS SI HAY O NO ASISTENCIAS
        if (this.checkboxMarcado) {
          pdf.setFontSize(8);
          pdf.text("PMR's: - ",15,80);
          pdf.text("MEDIOS: - ",15,85);
          pdf.text("NO SE REALIZAN ASISTENCIAS EN ESTE VUELO",15,100);
        } else if (this.medios === 'FURGONETA - 1 OPERARIO') {
          pdf.setFontSize(8);
          pdf.text("PMR's: " + this.pmrs,15,80);
          pdf.text("MEDIOS: " + this.medios,15,85);
          pdf.text(this.hpk + " HORA LLEGADA A PARKING ",15,95);
          pdf.text(this.calzosAvio + " HORA CALZOS DE AERONAVE ",15,100);
          pdf.text(this.aperturaAvio + " HORA ABREN PUERTAS DE AERONAVE",15,105);
          pdf.text(this.desembarqueAsistencias + " HORA DESEMBARQUE DE ASISTENCIAS",15,110);   
        } else {
          pdf.setFontSize(8);
          pdf.text("PMR's: " + this.pmrs,15,80);
          pdf.text("MEDIOS: " + this.medios,15,85);
          pdf.text(this.hpk + " HORA LLEGADA A PARKING ",15,95);
          pdf.text(this.calzosAvio + " HORA CALZOS DE AERONAVE ",15,100);
          pdf.text(this.hca + " HORA ACOPLE AMBULIFT",15,105);
          pdf.text(this.aperturaAvio + " HORA ABREN PUERTAS DE AERONAVE",15,110);
          pdf.text(this.desembarqueAsistencias + " HORA DESEMBARQUE DE ASISTENCIAS",15,115);
          pdf.text(this.hda + " HORA DESACOPLE AMBULIFT",15,120);
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
      this.checkboxMarcado = checkbox.checked;
    },
    // 
    t_llegada_medios(select) {
    const formulario = select.closest(".form_LLG");
    const campos = formulario.querySelectorAll(".campo input, .campo select");
    const medios = select.value;

    for (let i = 0; i < campos.length; i++) {
      if (campos[i] !== select) {
        if (medios === "FURGONETA - 1 OPERARIO") {
          if (campos[i].id === "hca" || campos[i].id === "hda") {
            campos[i].disabled = true;
          } else {
            campos[i].disabled = false;
          }
        } else {
          campos[i].disabled = false;
        }
      }
    }
  },
  },
  data() {
    return {
      compania: "",
      vuelo: "",
      fecha: "",
      hora: "",
      codigo: "19",
      dly: "",
      sta: "", // Inicializa con el valor adecuado
      std: "", // Inicializa con el valor adecuado
      eta: "", // Inicializa con el valor adecuado
      etd: "",
      noAsistenciasLlegadas: false,
      parkingLLG: "",
      pmrs: "",
      medios: "",
      hpk: "",
      calzosAvio: "",
      hca: "",
      aperturaAvio: "",
      desembarqueAsistencias: "",
      hda: "",
      checkboxMarcado: false,
    };
  },
};
</script>

<!-- -->

<style>
/* Estilos para los subformularios */
.narrowcast,
.data,
.form_LLG {
  background-color: #f9f9f9;
  border-radius: 10px;
  padding: 20px;
  margin-bottom: 20px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
 }

.form_LLG {
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
.form-control[disabled] {
  background-color: #b43348;
  cursor: not-allowed;
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
</style>