<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Git HUB</title>
    <link rel="stylesheet" href="style.css" type="text/css">
    <link href="" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
</head>
<body>

    <h1>Categorías de Reclamo</h1>
  
    <section>
      <div class="grid-container">
        <div class="grid-item" onclick="abrirModal('Asistencia y puntualidad')">Asistencia y puntualidad</div>
        <div class="grid-item" onclick="abrirModal('Conducta en clase')">Conducta en clase</div>
        <div class="grid-item" onclick="abrirModal('Rendimiento académico')">Rendimiento académico</div>
        <div class="grid-item" onclick="abrirModal('Presentación personal')">Presentación personal</div>
        <div class="grid-item" onclick="abrirModal('Relaciones interpersonales')">Relaciones interpersonales</div>
        <div class="grid-item" onclick="abrirModal('Faltas disciplinarias graves')">Faltas disciplinarias graves</div>
      </div>
    </section>
  
    <!-- Modal -->
    <div class="modal fade" id="modalReclamo" tabindex="-1" aria-hidden="true">
        <div class="modal-dialog">
          <div class="modal-content">
      
            <div class="modal-header">
              <h5 class="modal-title" id="modalTitulo">Nuevo Reclamo</h5>
              <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
            </div>
      
            <div class="modal-body">
              <form id="formReclamo">
                <div class="mb-3">
                  <label for="docente" class="form-label">Nombre del Docente</label>
                  <input type="text" class="form-control" id="docente" required>
                </div>
      
                <div class="mb-3">
                  <label for="materia" class="form-label">Materia</label>
                  <input type="text" class="form-control" id="materia" required>
                </div>
      
                <div class="mb-3">
                  <label for="alumno" class="form-label">Nombre del Alumno</label>
                  <input type="text" class="form-control" id="alumno" required>
                </div>
      
                <div class="mb-3">
                  <label for="telefono" class="form-label">Teléfono del Padre (con código país)</label>
                  <input type="tel" class="form-control" id="telefono" placeholder="Ej: 5491122334455" required>
                </div>
      
                <div class="mb-3">
                  <label for="descripcion" class="form-label">Descripción del Reclamo</label>
                  <textarea class="form-control" id="descripcion" rows="4" required></textarea>
                </div>
              </form>
            </div>
      
            <div class="modal-footer">
              <button class="btn btn-success" onclick="enviarWhatsApp()">Enviar por WhatsApp</button>
              <button class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
            </div>
      
          </div>
        </div>
      </div>
  
    <!-- JS Bootstrap + funcionalidad -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js"></script>
    <script>
      let categoriaSeleccionada = '';
  
      function abrirModal(categoria) {
        categoriaSeleccionada = categoria;
        document.getElementById('modalTitulo').innerText = `Reclamo: ${categoria}`;
        new bootstrap.Modal(document.getElementById('modalReclamo')).show();
      }
  
      function enviarWhatsApp() {
        const docente = document.getElementById('docente').value.trim();
        const materia = document.getElementById('materia').value.trim();
        const alumno = document.getElementById('alumno').value.trim();
        const telefono = document.getElementById('telefono').value.trim();
        const descripcion = document.getElementById('descripcion').value.trim();

        if (!docente || !materia || !alumno || !telefono || !descripcion) {
            alert("Por favor, completa todos los campos.");
            return;
        }

        const mensaje = `📢 *Reclamo de UTEPSA*\n\n👨‍🏫 Docente: ${docente}\n📘 Materia: ${materia}\n🧑 Alumno: ${alumno}\n📂 Categoría: ${categoriaSeleccionada}\n📝 Descripción: ${descripcion}`;
        const url = `https://wa.me/${telefono}?text=${encodeURIComponent(mensaje)}`;

        window.open(url, '_blank');
        }
    </script>
  </body>
  </html>
