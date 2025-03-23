<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Juego de Preguntas</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-900 text-white flex items-center justify-center min-h-screen">
  <div id="app" class="w-full max-w-xl bg-gray-800 rounded-lg p-6 shadow-lg">
    <h1 class="text-3xl font-bold text-center text-yellow-400 mb-6">Juego de Preguntas</h1>
    <img src="https://via.placeholder.com/300x150?text=Cuerpo+Humano" alt="Cuerpo Humano" class="mx-auto mb-6">
    <div id="question-section" class="text-center">
      <p id="question" class="text-xl font-medium mb-4"></p>
      <div id="answers" class="space-y-4"></div>
    </div>
    <button id="restart-btn" class="hidden bg-yellow-500 hover:bg-yellow-600 text-black px-4 py-2 rounded">Reiniciar</button>
  </div>

  <script>
    const questions = [
      {
        question: "¿Cuál es el órgano que bombea sangre en el cuerpo humano?",
        answers: ["Pulmones", "Corazón", "Hígado", "Cerebro"],
        correct: 1
      },
      {
        question: "¿Qué profesión se encarga de enseñar en las escuelas?",
        answers: ["Doctor", "Ingeniero", "Maestro", "Arquitecto"],
        correct: 2
      },
      {
        question: "¿Cuál es el sistema que transporta oxígeno y nutrientes por el cuerpo?",
        answers: ["Digestivo", "Respiratorio", "Circulatorio", "Nervioso"],
        correct: 2
      },
      {
        question: "¿Cuántos huesos tiene un adulto en su cuerpo?",
        answers: ["206", "300", "180", "250"],
        correct: 0
      },
      {
        question: "¿Qué órgano es responsable de la digestión de los alimentos?",
        answers: ["Cerebro", "Estómago", "Riñones", "Intestinos"],
        correct: 1
      },
      {
        question: "¿Qué profesión se encarga de curar a los animales?",
        answers: ["Veterinario", "Policía", "Chef", "Biólogo"],
        correct: 0
      },
      {
        question: "¿Cuál es el órgano más grande del cuerpo humano?",
        answers: ["Piel", "Hígado", "Cerebro", "Corazón"],
        correct: 0
      },
      {
        question: "¿Qué profesión diseña edificios?",
        answers: ["Abogado", "Arquitecto", "Mecánico", "Carpintero"],
        correct: 1
      },
      {
        question: "¿Cuántos pulmones tiene el cuerpo humano?",
        answers: ["Uno", "Dos", "Cuatro", "Tres"],
        correct: 1
      },
      {
        question: "¿Qué sistema del cuerpo se encarga de defendernos de enfermedades?",
        answers: ["Nervioso", "Inmunológico", "Muscular", "Esquelético"],
        correct: 1
      },
      {
        question: "¿Qué líquido transporta oxígeno por todo el cuerpo?",
        answers: ["Plasma", "Sangre", "Agua", "Linfático"],
        correct: 1
      },
      {
        question: "¿Qué parte del cuerpo humano se utiliza para escuchar?",
        answers: ["Nariz", "Oídos", "Manos", "Ojos"],
        correct: 1
      },
      {
        question: "¿Qué profesión se encarga de cuidar y proteger a la comunidad?",
        answers: ["Bombero", "Policía", "Enfermero", "Abogado"],
        correct: 1
      }
    ];

    let currentQuestionIndex = 0;

    const app = document.getElementById("app");
    const questionElement = document.getElementById("question");
    const answersElement = document.getElementById("answers");
    const restartButton = document.getElementById("restart-btn");

    function showQuestion() {
      const question = questions[currentQuestionIndex];
      questionElement.textContent = question.question;
      answersElement.innerHTML = "";
      question.answers.forEach((answer, index) => {
        const button = document.createElement("button");
        button.textContent = answer;
        button.className = "block w-full bg-blue-500 hover:bg-blue-600 text-white py-2 px-4 rounded";
        button.onclick = () => checkAnswer(index);
        answersElement.appendChild(button);
      });
    }

    function checkAnswer(selected) {
      const question = questions[currentQuestionIndex];
      if (selected === question.correct) {
        currentQuestionIndex++;
        if (currentQuestionIndex < questions.length) {
          showQuestion();
        } else {
          questionElement.textContent = "¡Felicitaciones! Has respondido todas las preguntas correctamente.";
          answersElement.innerHTML = "";
          restartButton.classList.remove("hidden");
        }
      } else {
        questionElement.textContent = "Respuesta incorrecta. Empiezas desde el inicio.";
        answersElement.innerHTML = "";
        restartButton.classList.remove("hidden");
      }
    }

    restartButton.onclick = () => {
      currentQuestionIndex = 0;
      restartButton.classList.add("hidden");
      showQuestion();
    };

    showQuestion();
  </script>
</body>
</html> 
