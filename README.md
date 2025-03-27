<!DOCTYPE html>
<html lang="es">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CASO CLÍNICO - Salud Ocupacional y Plaguicidas</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      color: #333;
      line-height: 1.6;
      max-width: 800px;
      margin: 20px auto;
      padding: 20px;
      background-color: #fff;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }

    h1, h2 {
      color: #1a5e63;
    }

    .section {
      display: none;
    }

    .active {
      display: block;
    }

    button {
      background-color: #1a5e63;
      color: #fff;
      padding: 10px 20px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 20px;
    }

    button:hover {
      background-color: #14494d;
    }

    .question {
      margin-top: 20px;
      font-weight: bold;
    }

    .options label {
      display: block;
      margin-bottom: 10px;
      cursor: pointer;
    }

    .result {
      background-color: #d9edf7;
      padding: 15px;
      border-radius: 5px;
      margin-top: 20px;
    }
  </style>
</head>

<body>

  <h1>CASO CLÍNICO INTERACTIVO</h1>
  <h2>Salud Ocupacional y Exposición a Plaguicidas</h2>

  <div id="intro" class="section active">
    <p>En salud ocupacional, la exposición a plaguicidas es una causa frecuente de alteraciones neuroconductuales en trabajadores agrícolas. En este caso, analizarás la historia clínica de un paciente con síntomas neurológicos inespecíficos y deberás evaluar la posible relación con su ambiente laboral.</p>
    <button onclick="nextSection('section1')">Iniciar caso</button>
  </div>

  <div id="section1" class="section">
    <h2>Consulta inicial</h2>
    <p><strong>Motivo de consulta:</strong> “Doctor, últimamente estoy olvidando las cosas, me siento mareado y me cuesta concentrarme”.</p>
    <p><strong>Paciente:</strong> Hombre de 42 años, trabajador agrícola con más de 15 años de experiencia en fumigación manual de cultivos de papa y hortalizas.</p>
    <button onclick="nextSection('section2')">Siguiente</button>
  </div>

  <div id="section2" class="section">
    <h2>Historia Ocupacional</h2>
    <ul>
      <li>Uso frecuente de plaguicidas organofosforados y carbamatos.</li>
      <li>Protección personal limitada o inexistente.</li>
      <li>Jornadas laborales de 10-12 horas.</li>
      <li>Referencias de otros compañeros con síntomas similares.</li>
    </ul>

    <div class="question">¿Qué hipótesis diagnóstica priorizarías?</div>
    <div class="options">
      <label><input type="radio" name="q1" value="a"> A) Trastorno de ansiedad generalizada</label>
      <label><input type="radio" name="q1" value="b"> B) Encefalopatía tóxica por exposición crónica a plaguicidas</label>
      <label><input type="radio" name="q1" value="c"> C) Depresión mayor</label>
    </div>

    <button onclick="checkAnswer1()">Confirmar respuesta</button>
    <div id="result1" class="result"></div>
  </div>

  <div id="section3" class="section">
    <h2>Evaluación Clínica</h2>
    <p>El examen neurológico muestra leve alteración de la memoria de trabajo y concentración, sin focalización neurológica ni alteraciones motoras.</p>
    <p><strong>Pruebas complementarias sugeridas:</strong></p>
    <ul>
      <li>Test neuroconductual breve</li>
      <li>Colinesterasa en sangre</li>
      <li>Perfil hepático y renal</li>
    </ul>

    <div class="question">¿Cuál sería el siguiente paso más apropiado?</div>
    <div class="options">
      <label><input type="radio" name="q2" value="a"> A) Iniciar antidepresivos de forma inmediata</label>
      <label><input type="radio" name="q2" value="b"> B) Solicitar la medición de colinesterasa y notificar a salud ocupacional</label>
      <label><input type="radio" name="q2" value="c"> C) Dar de alta y citar en 6 meses</label>
    </div>

    <button onclick="checkAnswer2()">Confirmar respuesta</button>
    <div id="result2" class="result"></div>
  </div>

  <div id="section4" class="section">
    <h2>Plan de Manejo y Recomendaciones</h2>
    <ul>
      <li>Confirmar la alteración de colinesterasa si se detecta disminución.</li>
      <li>Reportar el caso como sospecha de enfermedad de origen laboral.</li>
      <li>Realizar intervención en el lugar de trabajo:
        <ul>
          <li>Mejorar el uso de EPP</li>
          <li>Capacitación en manejo seguro de plaguicidas</li>
          <li>Vigilancia médica periódica</li>
        </ul>
      </li>
      <li>Derivación a neurología o salud mental si persisten síntomas.</li>
    </ul>

    <p><strong>Reflexión final:</strong> En salud ocupacional, identificar la relación entre los síntomas y el entorno laboral es clave para prevenir daños a largo plazo y proteger la salud de los trabajadores.</p>

    <button onclick="restart()">Volver a empezar</button>
  </div>

  <script>
    function nextSection(id) {
      document.querySelectorAll('.section').forEach(sec => sec.classList.remove('active'));
      document.getElementById(id).classList.add('active');
    }

    function checkAnswer1() {
      const answer = document.querySelector('input[name="q1"]:checked');
      const result = document.getElementById('result1');
      if (!answer) {
        result.textContent = "Selecciona una opción para continuar.";
        return;
      }
      if (answer.value === "b") {
        result.innerHTML = "✅ Correcto: La encefalopatía tóxica por exposición crónica a plaguicidas explica los síntomas neuroconductuales.";
      } else {
        result.innerHTML = "❌ Incorrecto. Revisa los factores de riesgo laborales y vuelve a intentarlo.";
        return;
      }
      setTimeout(() => nextSection('section3'), 2000);
    }

    function checkAnswer2() {
      const answer = document.querySelector('input[name="q2"]:checked');
      const result = document.getElementById('result2');
      if (!answer) {
        result.textContent = "Selecciona una opción para continuar.";
        return;
      }
      if (answer.value === "b") {
        result.innerHTML = "✅ Correcto: Es fundamental confirmar la afectación con pruebas y activar el protocolo de salud ocupacional.";
      } else {
        result.innerHTML = "❌ Incorrecto. La prioridad es evaluar la exposición y proteger la salud del trabajador.";
        return;
      }
      setTimeout(() => nextSection('section4'), 2000);
    }

    function restart() {
      nextSection('intro');
    }
  </script>

</body>

</html>
