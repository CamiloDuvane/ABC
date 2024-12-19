<html>
  <head>
    <base href="/">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Quiz Educacional Moçambicano</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
<style>
:root {
  --primary-color: #2196F3;
  --secondary-color: #FFC107;
  --text-color: #333;
  --background-color: #f5f5f5;
}
</style>
</head>
<body>
<div class="container" id="app">
  <div class="student-header">
    <h2>Bem-vindo, <span id="studentNameHeader"></span></h2>
    <div class="nav-menu">
      <button class="analytics-toggle" onclick="toggleAnalytics()">Ver Estatísticas</button>
    </div>
    
    <div class="analytics-grid" id="analyticsGrid" style="display: none;">
      <div class="analytics-card">
        <h3>Tempo Total Online</h3>
        <div class="time-spent" id="totalTimeSpent">0h 0m 0s</div>
      </div>
      <div class="analytics-card">
        <h3>Questões Respondidas</h3>
        <div class="time-spent" id="totalQuestions">0</div>
      </div>
      <div class="analytics-card">
        <h3>Disciplinas Estudadas</h3>
        <div class="time-spent" id="subjectsStudied">0</div>
      </div>
    </div>
  </div>

  <div id="loginForm" class="auth-container">
    <div id="errorMessage" style="display:none; color:red; text-align:center; margin:10px;"></div>
    <div class="login-form">
      <h2>Login</h2>
      <input type="text" id="username" placeholder="Nome de Usuário">
      <input type="password" id="accessCode" placeholder="Código de Acesso">
      <button class="button" onclick="handleLogin()">Entrar</button>
      <div class="auth-links">
        <a href="javascript:void(0)" onclick="showRegistration()">Registrar Nova Conta</a>
        <a href="javascript:void(0)" onclick="showPasswordRecovery()">Recuperar Senha</a>
      </div>
    </div>
  </div>

  <div id="subjectSelection" class="subject-grid">
    <div class="subject-card matematica" onclick="selectSubject(&apos;matematica&apos;)">Matemática</div>
    <div class="subject-card portugues" onclick="selectSubject(&apos;portugues&apos;)">Português</div>
    <div class="subject-card historia" onclick="selectSubject(&apos;historia&apos;)">História</div>
    <div class="subject-card quimica" onclick="selectSubject(&apos;quimica&apos;)">Química</div>
    <div class="subject-card biologia" onclick="selectSubject(&apos;biologia&apos;)">Biologia</div>
    <div class="subject-card contabilidade" onclick="selectSubject(&apos;contabilidade&apos;)">Contabilidade</div>
    <div class="subject-card fisica" onclick="selectSubject(&apos;fisica&apos;)">Física</div>
  </div>

  <div id="questionContainer" class="question-container">
    <div class="progress-bar">
      <div id="progressFill" class="progress-fill" style="width: 0%"></div>
    </div>
    <h3 id="questionText"></h3>
    <div id="questionImage"></div>
    <div id="options" class="options"></div>
    <button class="button" onclick="submitAnswer()">Próxima</button>
    <button class="button back-button" onclick="returnToSubjects()">Voltar para Disciplinas</button>
  </div>

  <div id="reportsContainer" class="reports-container">
    <div class="nav-menu">
      <h2>Relatório do Aluno</h2>
      <button class="button" onclick="returnToSubjects()">Voltar</button>
    </div>
    
    <div class="student-info">
      <div>
        <h3>Informação do Aluno</h3>
        <p><strong>Nome:</strong> <span id="studentName"></span></p>
        <p><strong>Email:</strong> <span id="studentEmail"></span></p>
        <p><strong>Telefone:</strong> <span id="studentPhone"></span></p>
        <p><strong>Data de Registro:</strong> <span id="registrationDate"></span></p>
      </div>
      <div>
        <h3>Estatísticas Gerais</h3>
        <p><strong>Total de Questões:</strong> <span id="totalQuestions"></span></p>
        <p><strong>Questões Corretas:</strong> <span id="correctAnswers"></span></p>
        <p><strong>Média Geral:</strong> <span id="averageScore"></span>%</p>
      </div>
    </div>

    <h3>Desempenho por Disciplina</h3>
    <div id="subjectScores">
      <!-- Score cards will be dynamically added here -->
    </div>

    <div class="history-section">
      <h3>Histórico de Atividades</h3>
      <table class="history-table">
        <thead>
          <tr>
            <th>Ordem</th>
            <th>Data/Hora</th>
            <th>Questões Respondidas</th>
            <th>Pontuação</th>
            <th>Tempo Gasto</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody id="historyTableBody">
          <!-- History rows will be added here dynamically -->
        </tbody>
      </table>
    </div>
  </div>
</div>

<footer class="footer">
  <div class="contact-info">
    <div class="contact-item">
      <i class="fab fa-facebook"></i>
      <p>Facebook</p>
      <a href="https://facebook.com/camilowilliam.duvane" target="_blank">Meu Perfil</a>
    </div>
    
    <div class="contact-item">
      <i class="fab fa-whatsapp"></i>
      <p>WhatsApp</p>
      <a href="https://wa.me/258842479404" target="_blank">+258 842479404</a>
    </div>
    
    <div class="contact-item">
      <i class="fas fa-envelope"></i>
      <p>Email</p>
      <a href="mailto:camilowilliam0@gmail.com">camilowilliam0@gmail.com</a>
    </div>
  
    <div class="payment-info">
      <h3>Informações de Pagamento</h3>
      <p><strong>M-Pesa:</strong> 842479404</p>
      <p><strong>BIM:</strong> 294440242</p>
    </div>
  </div>
</footer>

<script>let currentQuestion = 0;
let score = 0;
let questions = [];
let selectedOptionIndex = -1;
let startTime;
let sessionHistory = [];
let currentUser = null;
function initializeStudentDashboard() {
  startTime = new Date();
  const studentName = localStorage.getItem('studentName') || 'Aluno';
  document.getElementById('studentNameHeader').textContent = studentName;
  loadStudentHistory();
  updateAnalytics();
}
function loadStudentHistory() {
  const currentUser = JSON.parse(localStorage.getItem('currentUser'));
  if (!currentUser || !currentUser.activityHistory) return;

  // Group activities by subject
  const groupedActivities = currentUser.activityHistory.reduce((acc, activity) => {
    if (!acc[activity.subject]) {
      acc[activity.subject] = [];
    }
    acc[activity.subject].push(activity);
    return acc;
  }, {});

  const tableBody = document.getElementById('historyTableBody');
  tableBody.innerHTML = '';
  
  // Counter for subject groups
  let subjectCounter = 1;

  Object.entries(groupedActivities).forEach(([subject, activities]) => {
    // Create subject header row
    const subjectRow = document.createElement('tr');
    subjectRow.classList.add('subject-header');
    subjectRow.innerHTML = `
      <td>${subjectCounter}</td>
      <td colspan="5">${subject}</td>
    `;
    tableBody.appendChild(subjectRow);

    // Add activity rows for this subject
    activities.forEach(activity => {
      const activityDate = new Date(activity.date);
      const formattedDate = activityDate.toLocaleDateString();
      const formattedTime = activityDate.toLocaleTimeString();
      
      const row = document.createElement('tr');
      row.innerHTML = `
        <td></td>
        <td>${formattedDate} ${formattedTime}</td>
        <td>${activity.questionsAnswered}</td>
        <td>${activity.score}</td>
        <td>${activity.timeSpent}</td>
        <td>
          <button class="button" onclick="viewAnswers('${activity.id}')">Ver Respostas</button>
        </td>
      `;
      tableBody.appendChild(row);
    });

    subjectCounter++;
  });
}
function updateAnalytics() {
  const now = new Date();
  const timeSpentSeconds = Math.floor((now - startTime) / 1000);
  
  const hours = Math.floor(timeSpentSeconds / 3600);
  const minutes = Math.floor((timeSpentSeconds % 3600) / 60);
  const seconds = timeSpentSeconds % 60;
  
  document.getElementById('totalTimeSpent').textContent = 
    `${hours}h ${minutes}m ${seconds}s`;
    
  const answeredQuestions = sessionHistory.reduce((sum, session) => sum + session.questionsAnswered, 0);
  document.getElementById('totalQuestions').textContent = answeredQuestions;
  
  const uniqueSubjects = new Set(sessionHistory.map(session => session.subject));
  document.getElementById('subjectsStudied').textContent = uniqueSubjects.size;
}
function viewAnswers(sessionId) {
  const user = JSON.parse(localStorage.getItem('currentUser'));
  if (!user || !user.activityHistory) return;
  
  // Find the activity for this session
  const activity = user.activityHistory.find(a => a.id === sessionId);
  if (!activity) return;

  // Get all answers for this subject
  const subject = activity.subject;
  const subjectActivities = user.activityHistory.filter(a => a.subject === subject);
  const allSubjectAnswers = [];

  // Collect all answers for this subject
  subjectActivities.forEach(act => {
    const sessionAnswers = JSON.parse(sessionStorage.getItem(`answers_${act.id}`)) || [];
    if (sessionAnswers.length > 0) {
      allSubjectAnswers.push({
        date: new Date(act.date),
        answers: sessionAnswers
      });
    }
  });

  // Create modal with all answers grouped by date
  const modal = document.createElement('div');
  modal.className = 'answer-modal';
  modal.innerHTML = `
    <div class="answer-content">
      <span class="close-modal">&times;</span>
      <h3>Respostas da Disciplina: ${subject}</h3>
      <div class="answers-list"></div>
    </div>
  `;

  const answersList = modal.querySelector('.answers-list');
  
  // Sort answers by date, newest first
  allSubjectAnswers.sort((a, b) => b.date - a.date);

  // Add each session's answers
  allSubjectAnswers.forEach(session => {
    const sessionDate = session.date.toLocaleDateString();
    const sessionTime = session.date.toLocaleTimeString();
    
    const sessionDiv = document.createElement('div');
    sessionDiv.className = 'session-answers';
    sessionDiv.innerHTML = `
      <h4>Sessão - ${sessionDate} ${sessionTime}</h4>
    `;

    session.answers.forEach((answer, index) => {
      const answerItem = document.createElement('div');
      answerItem.className = `answer-item ${answer.isCorrect ? 'correct' : 'incorrect'}`;
      answerItem.innerHTML = `
        <p><strong>Pergunta ${index + 1}:</strong> ${answer.question}</p>
        <p><strong>Sua resposta:</strong> ${answer.selectedAnswer}</p>
        <p><strong>Resposta correta:</strong> ${answer.correctAnswer}</p>
      `;
      sessionDiv.appendChild(answerItem);
    });

    answersList.appendChild(sessionDiv);
  });

  document.body.appendChild(modal);
  modal.style.display = 'block';

  const closeBtn = modal.querySelector('.close-modal');
  closeBtn.onclick = () => {
    modal.remove();
  };
  
  modal.onclick = e => {
    if (e.target === modal) {
      modal.remove();
    }
  };
}
function handleLogin() {
  const username = document.getElementById('username').value;
  const accessCode = document.getElementById('accessCode').value;
  const errorMessage = document.getElementById('errorMessage');
  if (!username || !accessCode) {
    if (errorMessage) {
      errorMessage.style.display = 'block';
      errorMessage.textContent = 'Por favor preencha todos os campos';
    }
    return;
  }
  const registeredUser = JSON.parse(localStorage.getItem('registeredUser'));
  const user = {
    name: username,
    email: registeredUser ? registeredUser.email : 'student@example.com',
    phone: registeredUser ? registeredUser.phone : '',
    registrationDate: registeredUser ? registeredUser.registrationDate : new Date().toLocaleDateString(),
    stats: {
      totalQuestions: 0,
      correctAnswers: 0,
      averageScore: 0
    },
    activityHistory: []
  };
  localStorage.setItem('currentUser', JSON.stringify(user));
  localStorage.setItem('studentName', username);
  const loginForm = document.getElementById('loginForm');
  if (loginForm) loginForm.style.display = 'none';
  const elements = {
    studentHeader: document.querySelector('.student-header'),
    subjectSelection: document.getElementById('subjectSelection'),
    footer: document.querySelector('.footer')
  };
  Object.entries(elements).forEach(([key, element]) => {
    if (element) {
      if (key === 'studentHeader') {
        element.style.display = 'block';
        const studentNameHeader = document.getElementById('studentNameHeader');
        if (studentNameHeader) {
          studentNameHeader.textContent = username;
        }
      } else if (key === 'subjectSelection') {
        element.style.display = 'grid';
      } else if (key === 'footer') {
        element.classList.add('show');
      }
    }
  });
  initializeStudentDashboard();
}
function selectSubject(subject) {
  const startSessionTime = new Date();
  localStorage.setItem('currentSubject', subject);
  questions = getQuestionsBySubject(subject);
  if (!questions || !questions.length) {
    console.error('No questions found for subject:', subject);
    return;
  }
  const subjectSelection = document.getElementById('subjectSelection');
  const questionContainer = document.getElementById('questionContainer');
  if (!subjectSelection || !questionContainer) {
    console.error('Required containers not found');
    return;
  }
  subjectSelection.style.display = 'none';
  questionContainer.style.display = 'block';
  currentQuestion = 0;
  score = 0;
  selectedOptionIndex = -1;
  showQuestion(0);
  sessionHistory.push({
    subject: subject,
    startTime: startSessionTime,
    endTime: new Date(),
    questionsAnswered: 0,
    score: 0
  });
  updateAnalytics();
}
function getQuestionsBySubject(subject) {
  const questionSets = {
    matematica: [{
      question: "Qual é a área de um triângulo com base de 8 cm e altura de 5 cm?",
      options: ["20 cm²", "30 cm²", "40 cm²", "25 cm²"],
      correct: 3
    }, {
      question: "Resolva: 3x + 2 = 11. Qual é o valor de x?",
      options: ["2", "3", "4", "5"],
      correct: 1
    }, {
      question: "Qual é o valor de 7²?",
      options: ["14", "49", "21", "42"],
      correct: 1
    }, {
      question: "Qual é o perímetro de um quadrado com lado de 6 cm?",
      options: ["24 cm", "36 cm", "12 cm", "18 cm"],
      correct: 0
    }, {
      question: "Resolva: 4x - 8 = 0. Qual é o valor de x?",
      options: ["1", "2", "3", "4"],
      correct: 1
    }, {
      question: "Qual é o valor de √64?",
      options: ["6", "7", "8", "9"],
      correct: 2
    }, {
      question: "Se um círculo tem um raio de 7 cm, qual é a sua área? (π ≈ 3,14)",
      options: ["153,86 cm²", "140 cm²", "160 cm²", "170 cm²"],
      correct: 0
    }, {
      question: "Resolva: 2(x - 3) = 8. Qual é o valor de x?",
      options: ["5", "6", "7", "8"],
      correct: 2
    }, {
      question: "Qual é a forma geométrica que possui 6 faces quadradas iguais?",
      options: ["Cubo", "Cilindro", "Esfera", "Cone"],
      correct: 0
    }, {
      question: "Quantos graus tem um ângulo reto?",
      options: ["45°", "90°", "120°", "180°"],
      correct: 1
    }],
    portugues: [{
      question: "Identifique o substantivo abstrato na frase: 'A felicidade é uma conquista diária.'",
      options: ["Felicidade", "Conquista", "Diária", "Nenhuma das anteriores"],
      correct: 0
    }, {
      question: "Qual é a função da palavra 'rápido' em: 'Ele foi rápido para concluir a tarefa.'?",
      options: ["Substantivo", "Adjetivo", "Verbo", "Advérbio"],
      correct: 1
    }, {
      question: "Qual é o plural de 'pão'?",
      options: ["Pães", "Pãos", "Pões", "Paes"],
      correct: 0
    }, {
      question: "Complete a frase: 'Eu ________ estudar mais.'",
      options: ["devemos", "deveria", "dever", "deverei"],
      correct: 1
    }, {
      question: "Qual das frases contém uma metáfora?",
      options: ["Ele é forte como um leão", "A vida é um palco", "Estava tão feliz que parecia flutuar", "Estava tão quente quanto o deserto"],
      correct: 1
    }, {
      question: "Qual é o sujeito na frase: 'Os alunos estudam para o exame final'?",
      options: ["Os alunos", "Estudam", "Exame final", "Para o exame"],
      correct: 0
    }, {
      question: "Classifique a oração: 'Quando cheguei, ele já tinha saído.'",
      options: ["Coordenada", "Subordinada", "Simples", "Nominal"],
      correct: 1
    }, {
      question: "Identifique o verbo transitivo direto: 'Ela comprou um livro novo.'",
      options: ["Ela", "Comprou", "Livro", "Novo"],
      correct: 1
    }, {
      question: "Qual é o tempo verbal de 'Nós estudaremos juntos amanhã'?",
      options: ["Presente", "Passado", "Futuro do Presente", "Futuro do Pretérito"],
      correct: 2
    }, {
      question: "O que é uma interjeição?",
      options: ["Palavra que expressa emoção ou sentimento", "Palavra que liga orações", "Palavra que determina o verbo", "Palavra que indica lugar"],
      correct: 0
    }],
    historia: [{
      question: "Quem foi o primeiro presidente de Moçambique independente?",
      options: ["Joaquim Chissano", "Samora Machel", "Eduardo Mondlane", "Filipe Nyusi"],
      correct: 1
    }, {
      question: "Em que ano Moçambique conquistou sua independência?",
      options: ["1974", "1975", "1977", "1980"],
      correct: 1
    }, {
      question: "Qual foi o principal movimento de libertação nacional em Moçambique?",
      options: ["RENAMO", "FRELIMO", "MPLA", "PAIGC"],
      correct: 1
    }, {
      question: "Quem foi o fundador da FRELIMO?",
      options: ["Filipe Nyusi", "Eduardo Mondlane", "Samora Machel", "Joaquim Chissano"],
      correct: 1
    }, {
      question: "Qual é a data da assinatura do Acordo Geral de Paz?",
      options: ["4 de outubro de 1992", "7 de setembro de 1974", "25 de junho de 1975", "1 de dezembro de 1990"],
      correct: 0
    }],
    quimica: [{
      question: "Qual é o símbolo químico do oxigênio?",
      options: ["O", "Ox", "O₂", "O³"],
      correct: 0
    }, {
      question: "Qual é o número atômico do carbono?",
      options: ["6", "8", "12", "14"],
      correct: 0
    }, {
      question: "Qual é a fórmula química da água?",
      options: ["H₂O", "O₂H", "H₂O₂", "OH₂"],
      correct: 0
    }, {
      question: "Como se chama a reação em que uma substância ganha oxigênio?",
      options: ["Redução", "Oxidação", "Combustão", "Neutralização"],
      correct: 1
    }, {
      question: "Qual é o nome do processo de separação de misturas pelo calor?",
      options: ["Filtração", "Destilação", "Decantação", "Sublimação"],
      correct: 1
    }],
    biologia: [{
      question: "Qual é a unidade básica da vida?",
      options: ["Célula", "Tecidos", "Órgãos", "Organismos"],
      correct: 0
    }, {
      question: "Qual molécula é responsável pelo transporte de oxigênio no sangue?",
      options: ["Hemoglobina", "Glucose", "Insulina", "Lipídios"],
      correct: 0
    }, {
      question: "Qual grupo de organismos é responsável pela decomposição de matéria orgânica?",
      options: ["Fungos e bactérias", "Plantas", "Insetos", "Mamíferos"],
      correct: 0
    }, {
      question: "Qual é o tipo de reprodução em que apenas um organismo é necessário?",
      options: ["Sexuada", "Assexuada", "Alternada", "Dividida"],
      correct: 1
    }, {
      question: "Qual é o tipo de sangue considerado doador universal?",
      options: ["A", "B", "AB", "O negativo"],
      correct: 3
    }],
    fisica: [{
      question: "Qual é a unidade de força no Sistema Internacional?",
      options: ["Newton", "Joule", "Watt", "Pascal"],
      correct: 0
    }, {
      question: "Qual é a aceleração da gravidade na Terra?",
      options: ["9,8 m/s²", "10 m/s²", "9,8 km/s²", "8,9 m/s²"],
      correct: 0
    }, {
      question: "Qual é a unidade de potência no Sistema Internacional?",
      options: ["Watt", "Joule", "Newton", "Pascal"],
      correct: 0
    }, {
      question: "O que é energia cinética?",
      options: ["Energia de um corpo em movimento", "Energia armazenada", "Energia térmica", "Energia elétrica"],
      correct: 0
    }, {
      question: "Qual é a fórmula de Ohm?",
      options: ["V = IR", "F = ma", "E = mc²", "P = VI"],
      correct: 0
    }]
  };
  return questionSets[subject] || [];
}
function showQuestion(index) {
  if (index >= questions.length) {
    showResults();
    return;
  }
  const questionText = document.getElementById('questionText');
  const optionsContainer = document.getElementById('options');
  const progressFill = document.getElementById('progressFill');
  if (!questionText || !optionsContainer || !progressFill) {
    console.error('Required question elements not found');
    return;
  }
  const question = questions[index];
  questionText.textContent = question.question;
  optionsContainer.innerHTML = '';
  selectedOptionIndex = -1;
  question.options.forEach((option, i) => {
    const optionElement = document.createElement('div');
    optionElement.className = 'option';
    optionElement.textContent = option;
    optionElement.onclick = () => selectOption(i);
    optionsContainer.appendChild(optionElement);
  });
  const progress = index / questions.length * 100;
  progressFill.style.width = `${progress}%`;
}
function selectOption(optionIndex) {
  const options = document.querySelectorAll('.option');
  options.forEach(option => option.style.backgroundColor = '');
  options[optionIndex].style.backgroundColor = '#e3f2fd';
  selectedOptionIndex = optionIndex;
}
function submitAnswer() {
  const currentSessionId = Date.now().toString();
  const question = questions[currentQuestion];
  const selectedAnswer = question.options[selectedOptionIndex];
  const correctAnswer = question.options[question.correct];
  const isCorrect = selectedOptionIndex === question.correct;
  const sessionAnswers = JSON.parse(sessionStorage.getItem(`answers_${currentSessionId}`)) || [];
  sessionAnswers.push({
    question: question.question,
    selectedAnswer,
    correctAnswer,
    isCorrect
  });
  sessionStorage.setItem(`answers_${currentSessionId}`, JSON.stringify(sessionAnswers));
  if (isCorrect) {
    score++;
  }
  const currentUser = JSON.parse(localStorage.getItem('currentUser'));
  if (currentUser) {
    currentUser.stats.totalQuestions++;
    if (isCorrect) {
      currentUser.stats.correctAnswers++;
    }
    currentUser.stats.averageScore = Math.round(currentUser.stats.correctAnswers / currentUser.stats.totalQuestions * 100);
    const subject = localStorage.getItem('currentSubject');
    const now = new Date();
    const activity = {
      date: now.toISOString(),
      subject: subject,
      questionsAnswered: 1,
      score: isCorrect ? '100%' : '0%',
      timeSpent: '1m',
      id: currentSessionId
    };
    currentUser.activityHistory.push(activity);
    localStorage.setItem('currentUser', JSON.stringify(currentUser));
  }
  currentQuestion++;
  showQuestion(currentQuestion);
}
function showResults() {
  const container = document.getElementById('questionContainer');
  if (!container) return;
  const currentUser = JSON.parse(localStorage.getItem('currentUser'));
  if (currentUser) {
    const activity = {
      date: new Date().toISOString(),
      subject: localStorage.getItem('currentSubject') || 'Unknown',
      questionsAnswered: questions.length,
      score: `${Math.round(score / questions.length * 100)}%`,
      timeSpent: '10m',
      id: Date.now().toString()
    };
    currentUser.activityHistory.push(activity);
    localStorage.setItem('currentUser', JSON.stringify(currentUser));
  }
  container.innerHTML = `
    <h2>Resultados</h2>
    <p>Pontuação: ${score}/${questions.length}</p>
    <button class="button" onclick="returnToSubjects()">Voltar para Disciplinas</button>
    <button class="button" onclick="location.reload()">Jogar Novamente</button>
  `;
}
function showRegistration() {
  const container = document.querySelector('.auth-container');
  container.innerHTML = `
    <div class="login-form">
      <h2>Registrar Nova Conta</h2>
      <input type="text" id="newUsername" placeholder="Nome de Usuário">
      <input type="email" id="email" placeholder="Email">
      <input type="tel" id="phone" placeholder="Telefone"> 
      <input type="password" id="password" placeholder="Senha">
      <input type="password" id="confirmPassword" placeholder="Confirmar Senha">
      <button class="button" onclick="handleRegistration()">Registrar</button>
      <button class="button back-button" onclick="showLogin()">Voltar</button>
    </div>
  `;
}
function handleRegistration() {
  const username = document.getElementById('newUsername').value;
  const email = document.getElementById('email').value;
  const phone = document.getElementById('phone').value;
  const password = document.getElementById('password').value;
  const confirmPassword = document.getElementById('confirmPassword').value;
  if (!username || !email || !phone || !password || !confirmPassword) {
    alert('Por favor preencha todos os campos!');
    return;
  }
  if (password !== confirmPassword) {
    alert('As senhas não coincidem!');
    return;
  }
  const user = {
    name: username,
    email: email,
    phone: phone,
    registrationDate: new Date().toLocaleDateString(),
    stats: {
      totalQuestions: 0,
      correctAnswers: 0,
      averageScore: 0
    },
    activityHistory: []
  };
  localStorage.setItem('registeredUser', JSON.stringify(user));
  alert('Registro realizado com sucesso!');
  showLogin();
}
function showPasswordRecovery() {
  const container = document.querySelector('.auth-container');
  container.innerHTML = `
    <div class="login-form">
      <h2>Recuperar Senha</h2>
      <input type="email" id="recoveryEmail" placeholder="Email">
      <button class="button" onclick="handlePasswordRecovery()">Enviar</button>
      <button class="button back-button" onclick="showLogin()">Voltar</button>
    </div>
  `;
}
function showLogin() {
  const footer = document.querySelector('.footer');
  if (footer) {
    footer.classList.remove('show');
  }
  location.reload();
}
function returnToSubjects() {
  document.getElementById('reportsContainer').style.display = 'none';
  document.getElementById('questionContainer').style.display = 'none';
  document.getElementById('subjectSelection').style.display = 'grid';
}
function loadStudentData() {
  const currentUser = JSON.parse(localStorage.getItem('currentUser'));
  if (!currentUser) return;
  document.getElementById('studentName').textContent = currentUser.name;
  document.getElementById('studentEmail').textContent = currentUser.email;
  document.getElementById('studentPhone').textContent = currentUser.phone || 'Não informado';
  document.getElementById('registrationDate').textContent = currentUser.registrationDate;
  const studentInfo = document.querySelector('.student-info');
  if (studentInfo) {
    studentInfo.innerHTML = `
      <div>
        <h3>Informação do Aluno</h3>
        <p><strong>Nome:</strong> <span id="studentName">${currentUser.name}</span></p>
        <p><strong>Email:</strong> <span id="studentEmail">${currentUser.email}</span></p>
        <p><strong>Telefone:</strong> <span id="studentPhone">${currentUser.phone || 'Não informado'}</span></p>
        <p><strong>Data de Registro:</strong> <span id="registrationDate">${currentUser.registrationDate}</span></p>
      </div>
      <div>
        <h3>Estatísticas Gerais</h3>
        <p><strong>Total de Questões:</strong> <span id="totalQuestions">${currentUser.stats.totalQuestions}</span></p>
        <p><strong>Questões Corretas:</strong> <span id="correctAnswers">${currentUser.stats.correctAnswers}</span></p>
        <p><strong>Média Geral:</strong> <span id="averageScore">${currentUser.stats.averageScore}</span>%</p>
      </div>
    `;
  }
}
function toggleAnalytics() {
  const analyticsGrid = document.getElementById('analyticsGrid');
  if (!analyticsGrid) {
    console.error('Analytics grid element not found');
    return;
  }
  analyticsGrid.style.display = analyticsGrid.style.display === 'none' ? 'grid' : 'none';
}
function showReports() {
  document.getElementById('subjectSelection').style.display = 'none';
  document.getElementById('questionContainer').style.display = 'none';
  const reportsContainer = document.getElementById('reportsContainer');
  if (reportsContainer) {
    reportsContainer.style.display = 'block';
  }
  loadStudentData();
  const currentUser = JSON.parse(localStorage.getItem('currentUser'));
  if (currentUser && currentUser.activityHistory) {
    const tableBody = document.getElementById('historyTableBody');
    if (tableBody) {
      tableBody.innerHTML = '';
      currentUser.activityHistory.forEach(activity => {
        const row = document.createElement('tr');
        row.innerHTML = `
          <td>${new Date(activity.date).toLocaleDateString()}</td>
          <td>${activity.subject}</td>
          <td>${activity.questionsAnswered}</td>
          <td>${activity.score}</td>
          <td>${activity.timeSpent}</td>
          <td>
            <button class="button" onclick="viewAnswers('${activity.id}')">Ver Respostas</button>
          </td>
        `;
        tableBody.appendChild(row);
      });
    }
  }
  const subjectScores = document.getElementById('subjectScores');
  if (subjectScores && currentUser && currentUser.activityHistory) {
    const subjects = {};
    currentUser.activityHistory.forEach(activity => {
      if (!subjects[activity.subject]) {
        subjects[activity.subject] = {
          total: 0,
          correct: 0,
          attempts: 0
        };
      }
      subjects[activity.subject].attempts++;
      subjects[activity.subject].total += parseInt(activity.score);
    });
    
    subjectScores.innerHTML = '';
    Object.entries(subjects).forEach(([subject, stats]) => {
      const average = stats.total / stats.attempts;
      const scoreCard = document.createElement('div');
      scoreCard.className = 'analytics-card';
      scoreCard.style.cursor = 'pointer';
      scoreCard.onclick = () => showSubjectHistory(subject);
      scoreCard.innerHTML = `
        <h4>${subject}</h4>
        <p>Média: ${average.toFixed(1)}%</p>
        <p>Tentativas: ${stats.attempts}</p>
      `;
      subjectScores.appendChild(scoreCard);
    });
  }
}

// Add new function to show subject-specific history:
function showSubjectHistory(subject) {
  const currentUser = JSON.parse(localStorage.getItem('currentUser'));
  if (!currentUser || !currentUser.activityHistory) return;

  const subjectActivities = currentUser.activityHistory.filter(activity => 
    activity.subject.toLowerCase() === subject.toLowerCase()
  );

  const tableBody = document.getElementById('historyTableBody');
  if (!tableBody) return;

  tableBody.innerHTML = '';
  
  // Add subject header
  const subjectRow = document.createElement('tr');
  subjectRow.classList.add('subject-header');
  subjectRow.innerHTML = `
    <td>1</td>
    <td colspan="5">${subject}</td>
  `;
  tableBody.appendChild(subjectRow);

  // Add activities for this subject
  subjectActivities.forEach(activity => {
    const activityDate = new Date(activity.date);
    const formattedDate = activityDate.toLocaleDateString();
    const formattedTime = activityDate.toLocaleTimeString();
    
    const row = document.createElement('tr');
    row.innerHTML = `
      <td></td>
      <td>${formattedDate} ${formattedTime}</td>
      <td>${activity.questionsAnswered}</td>
      <td>${activity.score}</td>
      <td>${activity.timeSpent}</td>
      <td>
        <button class="button" onclick="viewAnswers('${activity.id}')">Ver Respostas</button>
      </td>
    `;
    tableBody.appendChild(row);
  });
}
setInterval(updateAnalytics, 1000);
document.querySelector('.nav-menu').innerHTML += `
  <button class="button" onclick="showReports()">Ver Relatório</button>
`;
document.addEventListener('DOMContentLoaded', () => {
  const elementsToHide = ['.student-header', '#subjectSelection', '#questionContainer', '#reportsContainer', '.footer'];
  elementsToHide.forEach(selector => {
    const element = document.querySelector(selector);
    if (element) {
      if (selector === '.footer') {
        element.classList.remove('show');
      } else {
        element.style.display = 'none';
      }
    }
  });
  const loginForm = document.getElementById('loginForm');
  if (loginForm) {
    loginForm.style.display = 'block';
  }
  localStorage.removeItem('currentUser');
  localStorage.removeItem('studentName');
});
</script>
</body>
</html>
