fetch('game.json')
  .then(res => res.json())
  .then(initGame);

let gameData, currentStage = 0, playerName;

function initGame(data) {
  gameData = data;
}

function startGame() {
  playerName = document.getElementById("player-name").value || "اللاعب";
  currentStage = 0;
  loadStage(currentStage);
}

function loadStage(i) {
  const stage = gameData.levels.version1.stages[i];
  if (!stage) {
    document.getElementById("game-container").innerHTML = `<h2>تهانينا ${playerName}! أكملت كل المراحل.</h2>`;
    return;
  }

  document.getElementById("level-info").innerText = stage.name;
  document.getElementById("ai-dialogue").innerText = `AI: ${gameData.ai.persona[Math.min(i, gameData.ai.persona.length-1)].dialogue}`;

  const qDiv = document.getElementById("questions-container");
  qDiv.innerHTML = "";
  stage.puzzles.forEach(q => {
    const btn = document.createElement("button");
    btn.innerText = q.question;
    btn.onclick = () => checkAnswer(q);
    qDiv.appendChild(btn);
  });
}

function checkAnswer(q) {
  const ans = prompt(`${q.question}\n${q.options.join(" | ")}`);
  if (ans === q.answer) {
    alert("ممتاز! إجابة صحيحة 🎉");
    currentStage++;
    loadStage(currentStage);
  } else {
    alert(`خطأ! الإجابة الصحيحة: ${q.answer}`);
  }
}
