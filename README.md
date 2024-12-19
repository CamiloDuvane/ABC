<html><head><base href="/">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Quiz Educacional Mo&#xe7;ambicano</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
<style>
:root {
  --primary-color: #2196F3;
  --secondary-color: #FFC107;
  --text-color: #333;
  --background-color: #f5f5f5;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-image: url('https://example.com/camilo-background.jpg');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  color: var(--text-color);
}

.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

.auth-container {
  max-width: 400px;
  margin: 50px auto;
  text-align: center;
}

.auth-links {
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
  font-size: 14px;
}

.auth-links a {
  color: var(--primary-color);
  text-decoration: none;
}

.auth-links a:hover {
  text-decoration: underline;
}

.login-form {
  background: white;
  padding: 40px;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  margin-top: 20px;
}

.login-form h2 {
  color: var(--primary-color);
  margin-bottom: 30px;
}

.login-form input {
  width: calc(100% - 24px);
  padding: 12px;
  margin: 10px 0;
  border: 2px solid #e0e0e0;
  border-radius: 6px;
  transition: border-color 0.3s;
}

.login-form select {
  width: calc(100% - 24px);
  padding: 12px;
  margin: 10px 0;
  border: 2px solid #e0e0e0;
  border-radius: 6px;
  transition: border-color 0.3s;
}

.login-form input:focus, .login-form select:focus {
  border-color: var(--primary-color);
  outline: none;
}

.button {
  background-color: var(--primary-color);
  color: white;
  padding: 12px 24px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.2s;
}

.button:hover {
  background-color: #1976D2;
}

.button.back-button {
  background-color: #9e9e9e;
  margin-top: 20px;
}

.button.back-button:hover {
  background-color: #757575;
}

.student-header {
  display: none; /* Hide header by default */
  background: rgba(255, 255, 255, 0.95);
  padding: 20px;
  border-radius: 12px;
  margin-bottom: 20px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.analytics-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

.analytics-card {
  background: white;
  padding: 15px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
  text-align: center;
  transition: transform 0.2s, box-shadow 0.2s;
}

.analytics-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

.time-spent {
  font-size: 24px;
  font-weight: bold;
  color: var(--primary-color);
}

.subject-grid {
  display: none; /* Hide subject grid by default */
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
  margin-top: 20px;
  animation: fadeIn 0.5s ease-out;
}

.subject-card {
  background: linear-gradient(145deg, #ffffff 0%, #f5f5f5 100%);
  padding: 30px;
  border-radius: 12px;
  text-align: center;
  cursor: pointer;
  transition: transform 0.2s;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

.subject-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 12px rgba(0,0,0,0.15);
}

.subject-card.matematica {
  background: linear-gradient(145deg, #ffffff 0%, #e3f2fd 100%);
  border-left: 4px solid #2196F3;
}

.subject-card.portugues {
  background: linear-gradient(145deg, #ffffff 0%, #f3e5f5 100%);
  border-left: 4px solid #9c27b0;
}

.subject-card.historia {
  background: linear-gradient(145deg, #ffffff 0%, #fff3e0 100%);
  border-left: 4px solid #ff9800;
}

.subject-card.quimica {
  background: linear-gradient(145deg, #ffffff 0%, #e8f5e9 100%);
  border-left: 4px solid #4caf50;
}

.subject-card.biologia {
  background: linear-gradient(145deg, #ffffff 0%, #e0f2f1 100%);
  border-left: 4px solid #009688;
}

.subject-card.contabilidade {
  background: linear-gradient(145deg, #ffffff 0%, #fce4ec 100%);
  border-left: 4px solid #e91e63;
}

.subject-card.fisica {
  background: linear-gradient(145deg, #ffffff 0%, #ede7f6 100%);
  border-left: 4px solid #673ab7;
}

.question-container {
  display: none; /* Hide question container by default */
  background: white;
  padding: 30px;
  border-radius: 8px;
  margin-top: 20px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.options {
  display: grid;
  gap: 10px;
  margin-top: 20px;
}

.option {
  padding: 15px;
  border: 2px solid #ddd;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.2s;
}

.option:hover {
  background-color: #f0f0f0;
}

.progress-bar {
  width: 100%;
  height: 10px;
  background-color: #ddd;
  border-radius: 5px;
  margin: 20px 0;
}

.progress-fill {
  height: 100%;
  background-color: var(--primary-color);
  border-radius: 5px;
  transition: width 0.3s;
}

.reports-container {
  display: none; /* Hide reports container by default */
  background: rgba(255, 255, 255, 0.95);
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  margin: 20px auto;
}

.history-section {
  margin-top: 30px;
  background: rgba(255, 255, 255, 0.95);
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.history-section h3 {
  margin-bottom: 20px;
  color: var(--primary-color);
}

.reports-container .history-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 15px;
}

.reports-container .history-table th,
.reports-container .history-table td {
  padding: 12px;
  text-align: left;
  border-bottom: 1px solid #eee;
}

.reports-container .history-table th {
  background-color: #f5f5f5;
  font-weight: bold;
  color: var(--text-color);
}

.history-table tr.subject-header {
  background-color: #f5f5f5;
  font-weight: bold;
}

.history-table tr.subject-header td {
  padding: 15px 12px;
}

.history-table tr:not(.subject-header) td:first-child {
  padding-left: 25px;
}

.footer {
  display: none; /* Show footer by default */
  padding: 20px;
  background: rgba(255, 255, 255, 0.95);
  border-radius: 12px;
  margin: 20px auto;
}

.contact-info {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
  margin-bottom: 20px;
  background: #f5f5f5;
  padding: 20px;
  border-radius: 8px;
}

.contact-item {
  padding: 10px;
  text-align: center;
}

.contact-item i {
  font-size: 24px;
  margin-bottom: 10px;
  color: var(--primary-color);
}

.payment-info {
  background: #f5f5f5;
  padding: 20px;
  border-radius: 8px;
  text-align: center;
}

.payment-info h3 {
  margin-top: 0;
  color: var(--primary-color);
  margin-bottom: 15px;
}

.payment-info p {
  margin: 5px 0;
}

.answer-modal {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  z-index: 1000;
}

.answer-content {
  position: relative;
  background: white;
  width: 80%;
  max-width: 800px;
  margin: 50px auto;
  padding: 20px;
  border-radius: 8px;
  max-height: 80vh;
  overflow-y: auto;
}

.answers-list {
  margin: 20px 0;
}

.answer-item {
  margin-bottom: 20px;
  padding: 15px;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
}

.answer-item.correct {
  border-left: 4px solid #4caf50;
}

.answer-item.incorrect {
  border-left: 4px solid #f44336;
}

.close-modal {
  position: absolute;
  right: 10px;
  top: 10px;
  font-size: 24px;
  cursor: pointer;
}

.session-answers {
  margin: 20px 0;
  padding: 15px;
  background: #f5f5f5;
  border-radius: 8px;
}

.session-answers h4 {
  margin: 0 0 15px 0;
  color: var(--primary-color);
  border-bottom: 1px solid #ddd;
  padding-bottom: 8px;
}

.answers-list {
  max-height: 70vh;
  overflow-y: auto;
  padding: 10px;
}

.answer-item {
  margin-bottom: 15px;
  padding: 15px;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
  background: white;
}

.answer-item.correct {
  border-left: 4px solid #4caf50;
}

.answer-item.incorrect {
  border-left: 4px solid #f44336;
}

.answer-modal .answer-content {
  position: relative;
  background: white;
  width: 90%;
  max-width: 800px;
  margin: 30px auto;
  padding: 25px;
  border-radius: 12px;
  max-height: 85vh;
  overflow-y: auto;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

.admin-panel {
  background: white;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  margin-top: 20px;
}

.admin-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  padding-bottom: 20px;
  border-bottom: 1px solid #eee;
}

.admin-nav {
  display: flex;
  gap: 10px;
}

.admin-button {
  background-color: var(--primary-color);
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.2s;
}

.admin-button:hover {
  background-color: #1976D2;
}

.admin-content {
  background: #f5f5f5;
  padding: 20px;
  border-radius: 8px;
  min-height: 400px;
}

.pending-item, .student-profile-card, .student-history-card {
  background: white;
  padding: 15px;
  margin-bottom: 15px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}

.student-profile-card p {
  display: flex;
  align-items: center;
  gap: 10px;
}

.approval-buttons {
  display: flex;
  gap: 10px;
  margin-top: 10px;
}

.approve-button {
  background-color: #4CAF50;
  color: white;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.reject-button {
  background-color: #f44336;
  color: white;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.reject-button:hover {
  background-color: #d32f2f;
}

.view-details-button, .view-answers-button {
  background-color: var(--primary-color);
  color: white;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 10px;
}

.subject-history {
  margin-top: 10px;
  padding-left: 20px;
}

.subject-section {
  margin-bottom: 30px;
  background: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.subject-section h4 {
  color: var(--primary-color);
  margin-bottom: 15px;
  padding-bottom: 10px;
  border-bottom: 2px solid var(--primary-color);
}

.session-answers {
  margin: 15px 0;
  padding: 15px;
  background: #f5f5f5;
  border-radius: 8px;
}

.answers-list {
  max-height: 400px;
  overflow-y: auto;
  padding: 10px;
}

.answer-item {
  margin-bottom: 15px;
  padding: 15px;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
  background: white;
}

.answer-item.correct {
  border-left: 4px solid #4caf50;
}

.answer-item.incorrect {
  border-left: 4px solid #f44336;
}

.answer-item p {
  margin: 5px 0;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
</head>
<body>
<div class="container" id="app">
  <div class="student-header" style="display: none;">
    <h2>Bem-vindo, <span id="studentNameHeader"></span></h2>
    <div class="nav-menu">
      <button class="analytics-toggle" onclick="toggleAnalytics()">Ver Estat&#xed;sticas</button>
    </div>
    
    <div class="analytics-grid" id="analyticsGrid" style="display: none;">
      <button class="button" onclick="returnFromAnalytics()">Voltar para Disciplinas</button>
      <div class="analytics-card">
        <h3>Tempo Total Online</h3>
        <div class="time-spent" id="totalTimeSpent">0h 0m 0s</div>
      </div>
      <div class="analytics-card">
        <h3>Quest&#xf5;es Respondidas</h3>
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
      <input type="text" id="username" placeholder="Nome de Usu&#xe1;rio">
      <input type="password" id="accessCode" placeholder="C&#xf3;digo de Acesso"> 
      <button class="button" onclick="handleLogin()">Entrar</button>
      <div class="auth-links">
        <a href="javascript:void(0)" onclick="showRegistration()">Registrar Nova Conta</a>
        <a href="javascript:void(0)" onclick="showPasswordRecovery()">Recuperar Senha</a>
      </div>
    </div>
  </div>

  <div id="registrationForm" class="auth-container" style="display: none;">
    <div class="login-form">
      <h2>Registro</h2>
      <input type="text" id="username" placeholder="Nome de Usu&#xe1;rio">
      <input type="email" id="email" placeholder="Email">
      <input type="tel" id="phone" placeholder="Telefone">
      <select id="academicLevel">
        <option value>Selecione o N&#xed;vel Acad&#xea;mico</option>
        <option value="fundamental">Ensino Fundamental</option>
        <option value="medio">Ensino M&#xe9;dio</option>
        <option value="superior">Ensino Superior</option>
        <option value="pos">P&#xf3;s-Gradua&#xe7;&#xe3;o</option>
      </select>
      <input type="password" id="password" placeholder="Senha">
      <button class="button" onclick="handleRegistration()">Registrar</button>
      <button class="button back-button" onclick="backToLogin()">Voltar</button>
    </div>
  </div>

  <div id="subjectSelection" class="subject-grid" style="display: none;">
    <div class="subject-card matematica" onclick="selectSubject(&apos;matematica&apos;)">Matem&#xe1;tica</div>
    <div class="subject-card portugues" onclick="selectSubject(&apos;portugues&apos;)">Portugu&#xea;s</div>
    <div class="subject-card historia" onclick="selectSubject(&apos;historia&apos;)">Hist&#xf3;ria</div>
    <div class="subject-card quimica" onclick="selectSubject(&apos;quimica&apos;)">Qu&#xed;mica</div>
    <div class="subject-card biologia" onclick="selectSubject(&apos;biologia&apos;)">Biologia</div>
    <div class="subject-card contabilidade" onclick="selectSubject(&apos;contabilidade&apos;)">Contabilidade</div>
    <div class="subject-card fisica" onclick="selectSubject(&apos;fisica&apos;)">F&#xed;sica</div>
  </div>

  <div id="questionContainer" class="question-container" style="display: none;">
    <div class="progress-bar">
      <div id="progressFill" class="progress-fill" style="width: 0%"></div>
    </div>
    <h3 id="questionText"></h3>
    <div id="questionImage"></div>
    <div id="options" class="options"></div>
    <button class="button" onclick="submitAnswer()">Pr&#xf3;xima</button>
    <button class="button back-button" onclick="returnToSubjects()">Voltar para Disciplinas</button>
  </div>

  <div id="reportsContainer" class="reports-container" style="display: none;">
    <div class="nav-menu">
      <h2>Relat&#xf3;rio do Aluno</h2>
      <button class="button" onclick="returnToSubjects()">Voltar</button>
    </div>
    
    <div class="student-info">
      <div>
        <h3>Informa&#xe7;&#xf5;es do Aluno</h3>
        <p><strong>Nome:</strong> <span id="studentName"></span></p>
        <p><strong>Email:</strong> <span id="studentEmail"></span></p>
        <p><strong>Telefone:</strong> <span id="studentPhone"></span></p>
        <p><strong>Data de Registro:</strong> <span id="registrationDate"></span></p>
      </div>
      <div>
        <h3>Estat&#xed;sticas Gerais</h3>
        <p><strong>Total de Quest&#xf5;es:</strong> <span id="totalQuestions"></span></p>
        <p><strong>Quest&#xf5;es Corretas:</strong> <span id="correctAnswers"></span></p>
        <p><strong>M&#xe9;dia Geral:</strong> <span id="averageScore"></span>%</p>
      </div>
    </div>

    <h3>Desempenho por Disciplina</h3>
    <div id="subjectScores">
      <!-- Score cards will be dynamically added here -->
    </div>

    <div class="history-section">
      <h3>Hist&#xf3;rio de Atividades</h3>
      <table class="history-table">
        <thead>
          <tr>
            <th>Ordem</th>
            <th>Data/Hora</th>
            <th>Quest&#xf5;es Respondidas</th>
            <th>Pontua&#xe7;&#xe3;o</th>
            <th>Tempo Gasto</th>
            <th>A&#xe7;&#xf5;es</th>
          </tr>
        </thead>
        <tbody id="historyTableBody">
          <!-- History rows will be added here dynamically -->
        </tbody>
      </table>
    </div>
  </div>
</div>

<footer class="footer" style="display: none;">
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
      <h3>Informa&#xe7;&#xf5;es de Pagamento</h3>
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
let subjectProgress = {};
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
  const groupedActivities = currentUser.activityHistory.reduce((acc, activity) => {
    if (!acc[activity.subject]) {
      acc[activity.subject] = [];
    }
    acc[activity.subject].push(activity);
    return acc;
  }, {});
  const tableBody = document.getElementById('historyTableBody');
  tableBody.innerHTML = '';
  let subjectCounter = 1;
  Object.entries(groupedActivities).forEach(([subject, activities]) => {
    const subjectRow = document.createElement('tr');
    subjectRow.classList.add('subject-header');
    subjectRow.innerHTML = `
      <td>${subjectCounter}</td>
      <td colspan="5">${subject}</td>
    `;
    tableBody.appendChild(subjectRow);
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
function toggleAnalytics() {
  const analyticsGrid = document.getElementById('analyticsGrid');
  const subjectSelection = document.getElementById('subjectSelection');
  if (analyticsGrid.style.display === 'none') {
    analyticsGrid.style.display = 'grid';
    subjectSelection.style.display = 'none';
    updateAnalytics();
  } else {
    analyticsGrid.style.display = 'none';
    subjectSelection.style.display = 'grid';
  }
}
function returnFromAnalytics() {
  const analyticsGrid = document.getElementById('analyticsGrid');
  const subjectSelection = document.getElementById('subjectSelection');
  analyticsGrid.style.display = 'none';
  subjectSelection.style.display = 'grid';
}
function formatTimeDuration(seconds) {
  const hours = Math.floor(seconds / 3600);
  const minutes = Math.floor(seconds % 3600 / 60);
  const remainingSeconds = seconds % 60;
  return `${hours}h ${minutes}m ${remainingSeconds}s`;
}
function updateAnalytics() {
  const now = new Date();
  const timeSpentSeconds = Math.floor((now - startTime) / 1000);
  document.getElementById('totalTimeSpent').textContent = formatTimeDuration(timeSpentSeconds);
  const totalQuestionsAnswered = sessionHistory.reduce((total, session) => {
    return total + (session.questionsAnswered || 0);
  }, 0);
  document.getElementById('totalQuestions').textContent = totalQuestionsAnswered;
  const uniqueSubjects = new Set(sessionHistory.map(session => session.subject));
  document.getElementById('subjectsStudied').textContent = uniqueSubjects.size;
}
function viewAnswers(sessionId) {
  const user = JSON.parse(localStorage.getItem('currentUser'));
  if (!user || !user.activityHistory) return;
  const activity = user.activityHistory.find(a => a.id === sessionId);
  if (!activity) return;
  const subject = activity.subject;
  const subjectActivities = user.activityHistory.filter(a => a.subject === subject);
  const allSubjectAnswers = [];
  subjectActivities.forEach(act => {
    const sessionAnswers = JSON.parse(sessionStorage.getItem(`answers_${act.id}`)) || [];
    if (sessionAnswers.length > 0) {
      allSubjectAnswers.push({
        date: new Date(act.date),
        answers: sessionAnswers
      });
    }
  });
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
  allSubjectAnswers.sort((a, b) => b.date - a.date);
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
function selectSubject(subject) {
  const startSessionTime = new Date();
  localStorage.setItem('currentSubject', subject);
  questions = getQuestionsBySubject(subject);
  if (!questions || !questions.length) {
    console.error('No questions found for subject:', subject);
    return;
  }
  if (subjectProgress[subject]) {
    currentQuestion = subjectProgress[subject];
  } else {
    currentQuestion = 0;
  }
  const studentHeader = document.querySelector('.student-header');
  const footer = document.querySelector('.footer');
  if (studentHeader) studentHeader.style.display = 'none';
  if (footer) footer.style.display = 'none';
  const subjectSelection = document.getElementById('subjectSelection');
  const questionContainer = document.getElementById('questionContainer');
  if (!subjectSelection || !questionContainer) {
    console.error('Required containers not found');
    return;
  }
  subjectSelection.style.display = 'none';
  questionContainer.style.display = 'block';
  score = 0;
  selectedOptionIndex = -1;
  showQuestion(currentQuestion);
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
      options: ["A vida é um rio.", "O sol está brilhando.", "A cidade é um local movimentado.", "A casa é azul."],
      correct: 0
    }, {
      question: "Qual é o significado da palavra 'não'?",
      options: ["Sim", "Não", "Talvez", "Nada"],
      correct: 1
    }, {
      question: "Identifique o verbo na frase: 'Eu estou estudando.'",
      options: ["Estou", "Estudando", "Eu", "Estudar"],
      correct: 1
    }, {
      question: "Qual é a forma correta de escrever a palavra 'ácido'?",
      options: ["Acido", "Acído", "Ácido", "Acidô"],
      correct: 2
    }, {
      question: "Qual é o significado da expressão 'tomar um banho'?",
      options: ["Lavar-se", "Comer", "Dormir", "Estudar"],
      correct: 0
    }]
  };
  return questionSets[subject];
}
function handleRegistration() {
  const username = document.getElementById('username').value;
  const email = document.getElementById('email').value;
  const phone = document.getElementById('phone').value;
  const academicLevel = document.getElementById('academicLevel').value;
  const password = document.getElementById('password').value;
  if (!username || !email || !phone || !academicLevel || !password) {
    alert('Por favor preencha todos os campos');
    return;
  }
  const registeredUser = {
    name: username,
    email: email,
    phone: phone,
    academicLevel: academicLevel,
    password: password,
    registrationDate: new Date().toLocaleDateString(),
    status: 'pending'
  };
  const pendingRegistrations = JSON.parse(localStorage.getItem('pendingRegistrations')) || [];
  pendingRegistrations.push(registeredUser);
  localStorage.setItem('pendingRegistrations', JSON.stringify(pendingRegistrations));
  const registrationForm = document.querySelector('div:last-child');
  registrationForm.remove();
  const loginForm = document.getElementById('loginForm');
  loginForm.style.display = 'block';
  const messageDiv = document.createElement('div');
  messageDiv.style.color = '#666';
  messageDiv.style.padding = '10px';
  messageDiv.style.marginTop = '10px';
  messageDiv.textContent = 'Seu registro está pendente de aprovação pelo administrador.';
  loginForm.appendChild(messageDiv);
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
  if (username === 'CWD' && accessCode === '6363') {
    showAdminPanel();
    return;
  }
  const approvedUsers = JSON.parse(localStorage.getItem('approvedUsers')) || [];
  const user = approvedUsers.find(u => u.name === username && u.password === accessCode);
  if (!user) {
    if (errorMessage) {
      errorMessage.style.display = 'block';
      errorMessage.textContent = 'Usuário não aprovado ou credenciais inválidas';
    }
    return;
  }
  localStorage.setItem('currentUser', JSON.stringify(user));
  localStorage.setItem('studentName', username);
  const loginForm = document.getElementById('loginForm');
  if (loginForm) loginForm.style.display = 'none';
  const subjectSelection = document.getElementById('subjectSelection');
  if (subjectSelection) subjectSelection.style.display = 'grid';
  const studentHeader = document.querySelector('.student-header');
  if (studentHeader) {
    studentHeader.style.display = 'block';
    const studentNameHeader = document.getElementById('studentNameHeader');
    if (studentNameHeader) {
      studentNameHeader.textContent = username;
    }
  }
  initializeStudentDashboard();
}
function showAdminPanel() {
  const loginForm = document.getElementById('loginForm');
  loginForm.style.display = 'none';
  const adminPanel = document.createElement('div');
  adminPanel.className = 'admin-panel';
  adminPanel.innerHTML = `
    <div class="admin-header">
      <h2>Painel de Administração</h2>
      <div class="admin-nav">
        <button class="admin-button" onclick="showPendingRegistrations()">Registros Pendentes</button>
        <button class="admin-button" onclick="showStudentList()">Lista de Alunos</button>
        <button class="admin-button" onclick="showStudentHistory()">Histórico</button>
        <button class="admin-button" onclick="adminLogout()">Sair</button>
      </div>
    </div>
    <div class="admin-content"></div>
  `;
  document.body.appendChild(adminPanel);
  showPendingRegistrations();
}
function showPendingRegistrations() {
  const pendingRegistrations = JSON.parse(localStorage.getItem('pendingRegistrations')) || [];
  const adminContent = document.querySelector('.admin-content');
  if (pendingRegistrations.length === 0) {
    adminContent.innerHTML = '<p>Não há registros pendentes de aprovação.</p>';
  } else {
    adminContent.innerHTML = '';
    pendingRegistrations.forEach((registration, index) => {
      const registrationCard = document.createElement('div');
      registrationCard.className = 'pending-item';
      registrationCard.innerHTML = `
        <h4>Registro ${index + 1}</h4>
        <p>Nome: ${registration.name}</p>
        <p>Email: ${registration.email}</p>
        <p>Data de Registro: ${registration.registrationDate}</p>
        <div class="approval-buttons">
          <button class="approve-button" onclick="approveRegistration(${index})">Aprovar</button>
          <button class="reject-button" onclick="rejectRegistration(${index})">Rejeitar</button>
        </div>
      `;
      adminContent.appendChild(registrationCard);
    });
  }
}
function showStudentList() {
  const approvedUsers = JSON.parse(localStorage.getItem('approvedUsers')) || [];
  const adminContent = document.querySelector('.admin-content');
  adminContent.innerHTML = '';
  approvedUsers.forEach((user, index) => {
    const userCard = document.createElement('div');
    userCard.className = 'student-profile-card';
    userCard.innerHTML = `
      <h4>Aluno ${index + 1}</h4>
      <p>Nome: ${user.name}</p>
      <p>Email: ${user.email}</p>
      <div class="button-group">
        <button class="view-details-button" onclick="viewStudentDetails(${index})">Ver Detalhes</button>
        <button class="view-answers-button" onclick="viewStudentAnswers(${index})">Ver Respostas</button>
        <button class="reject-button" onclick="deleteUser(${index})">Apagar Usuário</button>
      </div>
    `;
    adminContent.appendChild(userCard);
  });
}
function showStudentHistory() {
  const currentUser = JSON.parse(localStorage.getItem('currentUser'));
  if (!currentUser || !currentUser.activityHistory) return;
  const adminContent = document.querySelector('.admin-content');
  adminContent.innerHTML = '';
  const history = currentUser.activityHistory;
  history.forEach((session, index) => {
    const sessionCard = document.createElement('div');
    sessionCard.className = 'student-history-card';
    sessionCard.innerHTML = `
      <h4>Sessão ${index + 1}</h4>
      <p>Disciplina: ${session.subject}</p>
      <p>Data: ${new Date(session.date).toLocaleDateString()}</p>
      <p>Questões Respondidas: ${session.questionsAnswered}</p>
      <p>Pontuação: ${session.score}</p>
      <button class="view-answers-button" onclick="viewSessionAnswers(${index})">Ver Respostas</button>
    `;
    adminContent.appendChild(sessionCard);
  });
}
function approveRegistration(index) {
  const pendingRegistrations = JSON.parse(localStorage.getItem('pendingRegistrations'));
  const approvedUsers = JSON.parse(localStorage.getItem('approvedUsers')) || [];
  const registration = pendingRegistrations.splice(index, 1)[0];
  approvedUsers.push(registration);
  localStorage.setItem('pendingRegistrations', JSON.stringify(pendingRegistrations));
  localStorage.setItem('approvedUsers', JSON.stringify(approvedUsers));
  showPendingRegistrations();
}
function rejectRegistration(index) {
  const pendingRegistrations = JSON.parse(localStorage.getItem('pendingRegistrations'));
  pendingRegistrations.splice(index, 1);
  localStorage.setItem('pendingRegistrations', JSON.stringify(pendingRegistrations));
  showPendingRegistrations();
}
function adminLogout() {
  localStorage.removeItem('currentUser');
  const adminPanel = document.querySelector('.admin-panel');
  adminPanel.remove();
  const loginForm = document.getElementById('loginForm');
  loginForm.style.display = 'block';
}
function viewStudentDetails(index) {
  const approvedUsers = JSON.parse(localStorage.getItem('approvedUsers'));
  const user = approvedUsers[index];
  const adminContent = document.querySelector('.admin-content');
  adminContent.innerHTML = '';
  const userDetails = document.createElement('div');
  userDetails.className = 'student-profile-card';
  userDetails.innerHTML = `
    <h4>Detalhes do Aluno</h4>
    <p>Nome: ${user.name}</p>
    <p>Email: ${user.email}</p>
    <p>Telefone: ${user.phone || 'Não informado'}</p>
    <p>Nível Acadêmico: ${user.academicLevel || 'Não informado'}</p>
    <p>Senha: <span id="passwordField" style="filter: blur(4px)">${user.password}</span>
      <button onclick="togglePassword()" class="button">Mostrar/Ocultar Senha</button>
    </p>
    <button class="back-button" onclick="showStudentList()">Voltar</button>
  `;
  adminContent.appendChild(userDetails);
}
function viewSessionAnswers(index) {
  const currentUser = JSON.parse(localStorage.getItem('currentUser'));
  if (!currentUser || !currentUser.activityHistory) return;
  const adminContent = document.querySelector('.admin-content');
  adminContent.innerHTML = '';
  const session = currentUser.activityHistory[index];
  const sessionAnswers = JSON.parse(sessionStorage.getItem(`answers_${session.id}`)) || [];
  const answersList = document.createElement('div');
  answersList.className = 'answers-list';
  sessionAnswers.forEach((answer, index) => {
    const answerItem = document.createElement('div');
    answerItem.className = `answer-item ${answer.isCorrect ? 'correct' : 'incorrect'}`;
    answerItem.innerHTML = `
      <p><strong>Pergunta ${index + 1}:</strong> ${answer.question}</p>
      <p><strong>Sua resposta:</strong> ${answer.selectedAnswer}</p>
      <p><strong>Resposta correta:</strong> ${answer.correctAnswer}</p>
    `;
    answersList.appendChild(answerItem);
  });
  adminContent.appendChild(answersList);
  const backButton = document.createElement('button');
  backButton.className = 'back-button';
  backButton.textContent = 'Voltar';
  backButton.onclick = () => {
    showStudentHistory();
  };
  adminContent.appendChild(backButton);
}
function showRegistration() {
  const loginForm = document.getElementById('loginForm');
  loginForm.style.display = 'none';
  const registrationForm = document.createElement('div');
  registrationForm.className = 'auth-container';
  registrationForm.innerHTML = `
    <div class="login-form">
      <h2>Registro</h2>
      <input type="text" id="username" placeholder="Nome de Usuário">
      <input type="email" id="email" placeholder="Email">
      <input type="tel" id="phone" placeholder="Telefone">
      <select id="academicLevel">
        <option value="">Selecione o Nível Acadêmico</option>
        <option value="fundamental">Ensino Fundamental</option>
        <option value="medio">Ensino Médio</option>
        <option value="superior">Ensino Superior</option>
        <option value="pos">Pós-Graduação</option>
      </select>
      <input type="password" id="password" placeholder="Senha">
      <button class="button" onclick="handleRegistration()">Registrar</button>
      <button class="button back-button" onclick="backToLogin()">Voltar</button>
    </div>
  `;
  document.querySelector('.container').appendChild(registrationForm);
}
function showPasswordRecovery() {
  const loginForm = document.getElementById('loginForm');
  loginForm.style.display = 'none';
  const recoveryForm = document.createElement('div');
  recoveryForm.className = 'auth-container';
  recoveryForm.innerHTML = `
    <div class="login-form">
      <h2>Recuperar Senha</h2>
      <input type="email" id="recoveryEmail" placeholder="Email">
      <button class="button" onclick="handlePasswordRecovery()">Enviar</button>
      <button class="button back-button" onclick="backToLogin()">Voltar</button>
    </div>
  `;
  document.querySelector('.container').appendChild(recoveryForm);
}
function backToLogin() {
  const forms = document.querySelectorAll('.auth-container');
  forms.forEach(form => {
    if (form.id !== 'loginForm') {
      form.remove();
    }
  });
  document.getElementById('loginForm').style.display = 'block';
}
function handlePasswordRecovery() {
  const email = document.getElementById('recoveryEmail').value;
  alert('Um email de recuperação foi enviado para ' + email);
  backToLogin();
}
function viewStudentAnswers(index) {
  const approvedUsers = JSON.parse(localStorage.getItem('approvedUsers')) || [];
  const user = approvedUsers[index];
  const adminContent = document.querySelector('.admin-content');
  adminContent.innerHTML = `
    <h3>Respostas de ${user.name}</h3>
    <div class="answers-container"></div>
    <button class="back-button" onclick="showStudentList()">Voltar</button>
  `;
  const answersContainer = adminContent.querySelector('.answers-container');
  if (!user.activityHistory || user.activityHistory.length === 0) {
    answersContainer.innerHTML = '<p>Este usuário ainda não respondeu nenhuma questão.</p>';
    return;
  }
  const sessionsBySubject = user.activityHistory.reduce((acc, session) => {
    if (!acc[session.subject]) {
      acc[session.subject] = [];
    }
    acc[session.subject].push(session);
    return acc;
  }, {});
  Object.entries(sessionsBySubject).forEach(([subject, sessions]) => {
    const subjectDiv = document.createElement('div');
    subjectDiv.className = 'subject-section';
    subjectDiv.innerHTML = `<h4>Disciplina: ${subject}</h4>`;
    sessions.forEach((session, sessionIndex) => {
      const sessionDiv = document.createElement('div');
      sessionDiv.className = 'session-answers';
      sessionDiv.innerHTML = `
        <h4>Sessão ${sessionIndex + 1} - ${new Date(session.date).toLocaleDateString()}</h4>
        <p>Pontuação: ${session.score}%</p>
      `;
      const sessionAnswers = JSON.parse(sessionStorage.getItem(`answers_${session.id}`)) || [];
      if (sessionAnswers.length > 0) {
        const answersList = document.createElement('div');
        answersList.className = 'answers-list';
        sessionAnswers.forEach((answer, answerIndex) => {
          const answerItem = document.createElement('div');
          answerItem.className = `answer-item ${answer.isCorrect ? 'correct' : 'incorrect'}`;
          answerItem.innerHTML = `
            <p><strong>Pergunta ${answerIndex + 1}:</strong> ${answer.question}</p>
            <p><strong>Resposta do aluno:</strong> ${answer.selectedAnswer}</p>
            <p><strong>Resposta correta:</strong> ${answer.correctAnswer}</p>
          `;
          answersList.appendChild(answerItem);
        });
        sessionDiv.appendChild(answersList);
      } else {
        sessionDiv.innerHTML += '<p>Não há detalhes das respostas disponíveis para esta sessão.</p>';
      }
      subjectDiv.appendChild(sessionDiv);
    });
    answersContainer.appendChild(subjectDiv);
  });
}
function showQuestion(index) {
  if (!questions[index]) return;
  const questionText = document.getElementById('questionText');
  const optionsDiv = document.getElementById('options');
  const progressFill = document.getElementById('progressFill');
  questionText.textContent = questions[index].question;
  optionsDiv.innerHTML = '';
  questions[index].options.forEach((option, i) => {
    const optionDiv = document.createElement('div');
    optionDiv.className = 'option';
    optionDiv.textContent = option;
    optionDiv.onclick = () => selectOption(i);
    optionsDiv.appendChild(optionDiv);
  });
  const progress = (index + 1) / questions.length * 100;
  progressFill.style.width = `${progress}%`;
}
function selectOption(index) {
  selectedOptionIndex = index;
  const options = document.querySelectorAll('.option');
  options.forEach((option, i) => {
    option.style.backgroundColor = i === index ? '#e3f2fd' : '';
  });
}
function submitAnswer() {
  if (selectedOptionIndex === -1) {
    alert('Por favor selecione uma opção');
    return;
  }
  const currentQuestionObj = questions[currentQuestion];
  const isCorrect = selectedOptionIndex === currentQuestionObj.correct;
  if (isCorrect) score++;
  const answerData = {
    question: currentQuestionObj.question,
    selectedAnswer: currentQuestionObj.options[selectedOptionIndex],
    correctAnswer: currentQuestionObj.options[currentQuestionObj.correct],
    isCorrect: isCorrect
  };
  const sessionId = new Date().getTime().toString();
  const answersKey = `answers_${sessionId}`;
  const previousAnswers = JSON.parse(sessionStorage.getItem(answersKey)) || [];
  previousAnswers.push(answerData);
  sessionStorage.setItem(answersKey, JSON.stringify(previousAnswers));
  currentQuestion++;
  const subject = localStorage.getItem('currentSubject');
  subjectProgress[subject] = currentQuestion;
  selectedOptionIndex = -1;
  if (currentQuestion < questions.length) {
    showQuestion(currentQuestion);
  } else {
    finishQuiz();
  }
}
function finishQuiz() {
  const subject = localStorage.getItem('currentSubject');
  const finalScore = Math.round(score / questions.length * 100);
  const sessionData = {
    id: new Date().getTime().toString(),
    subject: subject,
    date: new Date().toISOString(),
    questionsAnswered: questions.length,
    score: finalScore,
    timeSpent: getTimeSpent()
  };
  const currentUser = JSON.parse(localStorage.getItem('currentUser'));
  if (currentUser) {
    if (!currentUser.activityHistory) currentUser.activityHistory = [];
    currentUser.activityHistory.push(sessionData);
    localStorage.setItem('currentUser', JSON.stringify(currentUser));
  }
  subjectProgress[subject] = 0;
  if (confirm(`Quiz finalizado! Pontuação: ${finalScore}%\n\nDeseja começar novamente?`)) {
    currentQuestion = 0;
    score = 0;
    selectedOptionIndex = -1;
    showQuestion(currentQuestion);
  } else {
    returnToSubjects();
  }
}
function getTimeSpent() {
  const now = new Date();
  const session = sessionHistory[sessionHistory.length - 1];
  const timeSpent = Math.floor((now - new Date(session.startTime)) / 1000);
  return formatTimeDuration(timeSpent);
}
function returnToSubjects() {
  const subject = localStorage.getItem('currentSubject');
  if (subject && currentQuestion > 0) {
    subjectProgress[subject] = currentQuestion;
  }
  document.getElementById('questionContainer').style.display = 'none';
  document.getElementById('subjectSelection').style.display = 'grid';
  document.querySelector('.student-header').style.display = 'block';
  document.querySelector('.footer').style.display = 'block';
}
function togglePassword() {
  const passwordField = document.getElementById('passwordField');
  if (passwordField.style.filter === 'blur(4px)') {
    passwordField.style.filter = 'none';
  } else {
    passwordField.style.filter = 'blur(4px)';
  }
}
function deleteUser(index) {
  if (confirm('Tem certeza que deseja apagar este usuário? Esta ação não pode ser desfeita.')) {
    const approvedUsers = JSON.parse(localStorage.getItem('approvedUsers')) || [];
    approvedUsers.splice(index, 1);
    localStorage.setItem('approvedUsers', JSON.stringify(approvedUsers));
    showStudentList();
  }
}</script>
</body>
</html>
