<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>7th Grade Science Test Review</title>
    <style>
        :root {
            --primary: #3182ce;
            --primary-dark: #2b6cb0;
            --secondary: #4a5568;
            --dark: #1a202c;
            --light: #f7fafc;
            --success: #38a169;
            --danger: #e53e3e;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #edf2f7;
            color: var(--dark);
            margin: 0;
            padding: 0;
        }

        header {
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            color: white;
            text-align: center;
            padding: 30px 20px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        header h1 {
            margin: 0;
            font-size: 2.2rem;
        }

        header p {
            margin: 10px 0 0 0;
            opacity: 0.9;
            font-size: 1.1rem;
        }

        .container {
            max-width: 900px;
            margin: 40px auto;
            padding: 0 20px;
        }

        /* Menu Selection Screen */
        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
            margin-top: 20px;
        }

        .menu-card {
            background: white;
            border-radius: 12px;
            padding: 30px;
            text-align: center;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
            border: 1px solid #e2e8f0;
        }

        .menu-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
            border-color: var(--primary);
        }

        .menu-card h2 {
            margin-top: 0;
            color: var(--primary-dark);
        }

        .menu-card p {
            color: #718096;
            font-size: 1rem;
            line-height: 1.5;
            margin-bottom: 25px;
        }

        .main-btn {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 12px 24px;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 8px;
            cursor: pointer;
            transition: background 0.2s;
        }

        .main-btn:hover {
            background-color: var(--primary-dark);
        }

        /* Workspace Panels */
        .view-panel {
            display: none;
            background: white;
            border-radius: 12px;
            padding: 30px;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
            animation: fadeIn 0.4s ease;
        }

        .back-bar {
            display: flex;
            justify-content: flex-start;
            margin-bottom: 20px;
        }

        .back-btn {
            background-color: #e2e8f0;
            color: var(--dark);
            border: none;
            padding: 8px 16px;
            font-weight: 600;
            border-radius: 6px;
            cursor: pointer;
        }

        .back-btn:hover {
            background-color: #cbd5e0;
        }

        /* --- QUIZ STYLES --- */
        .question-box { display: none; }
        .question-box.active { display: block; }
        .question-text { font-size: 1.2rem; font-weight: 600; margin-bottom: 20px; }
        .options-list { list-style: none; padding: 0; }
        .option-item {
            background: var(--light);
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            padding: 14px;
            margin-bottom: 12px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.2s;
        }
        .option-item:hover { border-color: var(--primary); background: #ebf8ff; }
        .option-item.correct { background-color: #c6f6d5 !important; border-color: var(--success) !important; color: #22543d; font-weight: bold; }
        .option-item.wrong { background-color: #fed7d7 !important; border-color: var(--danger) !important; color: #742a2a; }
        .quiz-controls { display: flex; justify-content: space-between; margin-top: 25px; }
        .progress-text { font-weight: bold; color: #718096; margin-bottom: 15px; text-align: right; }
        .multi-info { font-style: italic; color: #dd6b20; font-weight: bold; display: block; margin-bottom: 10px; }

        /* --- FLASHCARD STYLES --- */
        .flashcard-wrapper { max-width: 550px; margin: 0 auto; perspective: 1000px; }
        .card-container {
            width: 100%;
            height: 300px;
            position: relative;
            transform-style: preserve-3d;
            transition: transform 0.5s ease;
            cursor: pointer;
        }
        .card-container.flipped { transform: rotateY(180deg); }
        .card-side {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 15px;
            box-shadow: 0 6px 15px rgba(0,0,0,0.1);
            padding: 30px;
            font-size: 1.25rem;
            box-sizing: border-box;
            text-align: center;
            line-height: 1.5;
        }
        .card-front { background: linear-gradient(135deg, var(--primary), var(--primary-dark)); color: white; }
        .card-back { background: white; color: var(--dark); transform: rotateY(180deg); border: 3px dashed var(--primary); }
        .card-controls { display: flex; justify-content: space-around; align-items: center; margin-top: 30px; }
        .hint { font-size: 0.8rem; position: absolute; bottom: 15px; opacity: 0.8; letter-spacing: 1px; }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

<header>
    <h1>7th Grade Physical Science Review</h1>
    <p>Matter, Elements, Compounds, Mixtures, pH, & Chemical Changes</p>
</header>

<div class="container">

    <div id="menu-view" class="menu-grid">
        <div class="menu-card" onclick="switchView('quiz-view')">
            <h2>📝 Interactive Quiz</h2>
            <p>Test your knowledge with an interactive 20-question review. Get instant correction and see your final score!</p>
            <button class="main-btn">Start Quiz</button>
        </div>

        <div class="menu-card" onclick="switchView('flashcard-view')">
            <h2>🎴 Study Flashcards</h2>
            <p>Review key terms, pH concepts, and properties of matter at your own pace with 3D flipping study cards.</p>
            <button class="main-btn">Open Flashcards</button>
        </div>
    </div>

    <div id="quiz-view" class="view-panel">
        <div class="back-bar">
            <button class="back-btn" onclick="switchView('menu-view')">⬅ Back to Main Menu</button>
        </div>
        <div id="quiz-body">
            <div class="progress-text" id="quiz-progress">Question 1 of 20</div>
            
            <div id="questions-container"></div>

            <div class="quiz-controls">
                <button class="main-btn" style="background-color: var(--secondary);" id="quizPrev" onclick="navigateQuiz(-1)" disabled>Previous</button>
                <button class="main-btn" id="quizNext" onclick="navigateQuiz(1)">Next</button>
            </div>
        </div>
        <div id="quiz-score-screen" style="display:none; text-align:center;">
            <h2>Review Complete! 🎉</h2>
            <p style="font-size: 1.4rem; margin: 20px 0;">Your Score: <span id="final-score">0</span> / 20</p>
            <button class="main-btn" onclick="resetQuiz()">Try Again</button>
        </div>
    </div>

    <div id="flashcard-view" class="view-panel">
        <div class="back-bar">
            <button class="back-btn" onclick="switchView('menu-view')">⬅ Back to Main Menu</button>
        </div>
        
        <div class="flashcard-wrapper">
            <div class="card-container" id="flashcard" onclick="flipCard()">
                <div class="card-side card-front">
                    <span id="front-text">Loading...</span>
                    <div class="hint">CLICK TO FLIP</div>
                </div>
                <div class="card-side card-back">
                    <span id="back-text">Loading...</span>
                    <div class="hint" style="color: #718096;">CLICK TO FLIP BACK</div>
                </div>
            </div>
            <div class="card-controls">
                <button class="main-btn" onclick="changeCard(-1)">⬅ Prev</button>
                <span id="card-counter" style="font-weight:bold; color: var(--secondary);">Card 1 of 20</span>
                <button class="main-btn" onclick="changeCard(1)">Next ➡</button>
            </div>
        </div>
    </div>

</div>

<script>
    // DATA SOURCE FOR BOTH MODULES
    const coreData = [
        { q: "Container 1 holds a pure substance made of only one type of atom that cannot be broken down. Container 2 holds two different types of atoms chemically bonded. Container 3 holds salt and pepper tossed together. How are they classified?", a: "Container 1 = Element\nContainer 2 = Compound\nContainer 3 = Mixture", options: ["Container 1: Element | Container 2: Compound | Container 3: Mixture", "Container 1: Mixture | Container 2: Element | Container 3: Compound", "Container 1: Compound | Container 2: Mixture | Container 3: Element", "Container 1: Element | Container 2: Mixture | Container 3: Compound"], correct: 0, type: "single" },
        { q: "To be classified as \"matter,\" a substance must meet which two requirements?", a: "It must have mass and take up space (volume).", options: ["It must have mass and take up space (volume).", "It must be visible and have a solid shape.", "It must be able to conduct heat and electricity.", "It must be a pure element found on the periodic table."], correct: 0, type: "single" },
        { q: "Which of the following is the best definition of an element?", a: "A pure substance that consists of only one type of atom.", options: ["A pure substance that consists of only one type of atom.", "A substance made of two or more types of atoms chemically bonded.", "A mixture of different substances that can be physically separated.", "Any liquid substance that can dissolve other materials."], correct: 0, type: "single" },
        { q: "Which of these substances is NOT an element found on the periodic table?", a: "Table salt is a compound (Sodium Chloride). Pure gold, iron, and oxygen are elements.", options: ["Table Salt", "Gold", "Iron", "Oxygen"], correct: 0, type: "single" },
        { q: "A scientist tests two liquids. Liquid A has a pH of 2, and Liquid B has a pH of 5. Which statement is correct?", a: "Liquid A is more acidic. Lower numbers on the pH scale mean a stronger acid.", options: ["Liquid A is more acidic than Liquid B.", "Liquid B is more acidic than Liquid A.", "Both liquids are basic.", "Liquid A is a base and Liquid B is an acid."], correct: 0, type: "single" },
        { q: "A student creates a table of pH values for household items. Which item is the strongest BASE?\n• Bleach: pH 13 | • Soap: pH 10 | • Milk: pH 6 | • Lemon Juice: pH 2", a: "Bleach (pH 13) is the strongest base because it has the highest number above 7.", options: ["Bleach: pH 13", "Soap: pH 10", "Milk: pH 6", "Lemon Juice: pH 2"], correct: 0, type: "single" },
        { q: "If you have a 1 cm³ cube of gold and a 1 cm³ cube of aluminum, why does the gold cube feel much heavier?", a: "Gold has a higher density (more mass packed into the same volume).", options: ["Gold has a higher density.", "Gold is more malleable.", "The gold cube has a larger volume.", "Gold is a better conductor."], correct: 0, type: "single" },
        { q: "Hammering copper into a sheet demonstrates [1]. Stretching aluminum into wires demonstrates [2]. Attaching a battery to look at electric flow tests [3]. Melting metals together to make bronze creates an [4].", a: "[1] malleable, [2] ductile, [3] conductivity, [4] alloy", options: ["[1] malleable, [2] ductile, [3] conductivity, [4] alloy", "[1] ductile, [2] malleable, [3] alloy, [4] conductivity", "[1] conductivity, [2] alloy, [3] malleable, [4] ductile", "[1] alloy, [2] conductivity, [3] ductile, [4] malleable"], correct: 0, type: "single" },
        { q: "Which of these is a typical property of a non-metal? (Select TWO)", a: "They are brittle and are poor conductors of heat/electricity.", options: ["Poor conductor of heat.", "Brittle", "High electrical conductivity.", "Shiny, metallic luster."], correctIndices: [0, 1], type: "multi" },
        { q: "What makes metalloids unique compared to metals and non-metals?", a: "They have properties of both metals and non-metals.", options: ["They have properties of both metals and non-metals.", "They are the only substances that have mass.", "They are always gases at room temperature.", "They cannot react with other elements."], correct: 0, type: "single" },
        { q: "If you mix salt and pepper together in a bowl, why is this considered a mixture and not a compound?", a: "They can be physically separated and are not chemically bonded.", options: ["They can be physically separated and are not chemically bonded.", "They are both solids.", "A new substance was formed.", "The salt dissolves the pepper."], correct: 0, type: "single" },
        { q: "A student is analyzing four samples. Based on the information provided, which sample is most likely a mixture?", a: "Sample B: White Solid; Can be separated by dissolving and evaporation.", options: ["Sample B: White Solid; Can be separated by dissolving and evaporation.", "Sample A: Silver Solid; Cannot be separated.", "Sample C: Clear Liquid; Separated by electrolysis (chemical).", "Sample D: Red Solid; Cannot be separated."], correct: 0, type: "single" },
        { q: "A model of a water molecule shows one oxygen atom chemically bonded to two hydrogen atoms. Why is water classified as a compound and not an element?", a: "It contains two different types of atoms chemically bonded together.", options: ["It contains two different types of atoms chemically bonded", "It can exist as a solid, liquid, or gas.", "It is a transparent liquid.", "It can be separated by simple filtration."], correct: 0, type: "single" },
        { q: "A student shines a flashlight through two clear liquids. In Liquid X, the beam is invisible. In Liquid Y, the beam is clearly visible. Which classification is correct?", a: "Liquid X is a solution; Liquid Y is a colloid (Tyndall Effect).", options: ["Liquid X is a solution; Liquid Y is a colloid.", "Liquid X is a mixture; Liquid Y is a pure substance.", "Liquid X is a base; Liquid Y is an acid.", "Liquid X is an element; Liquid Y is a compound."], correct: 0, type: "single" },
        { q: "Which of the following is an example of a physical change?", a: "An ice cube melting into liquid water. (Changes states of matter, but stays water).", options: ["An ice cube melting into liquid water.", "Baking a cake in the oven.", "A piece of wood burning in a fireplace.", "An iron nail rusting."], correct: 0, type: "single" },
        { q: "A student heats a sample of ice. A graph shows the temperature staying at 0°C for several minutes while the ice is melting. Which statement is true?", a: "A physical change is occurring because the substance is changing state.", options: ["A physical change is occurring because the substance is changing state.", "The mass of the ice is disappearing.", "A chemical change is occurring.", "The temperature plateau means the reaction has stopped."], correct: 0, type: "single" },
        { q: "A student mixes two clear liquids. Which observation would provide the strongest evidence that a chemical change has occurred? (Select TWO)", a: "1. Bubbles of gas/color change.\n2. A solid precipitate forms.", options: ["Bubbles of gas formed and the solution changed color.", "A solid precipitate forms at the bottom of the beaker", "The temperature of the beaker remain exactly the same", "The two liquids mixed together completely"], correctIndices: [0, 1], type: "multi" },
        { q: "CER Scenario: A 10g iron nail is left outside. Two weeks later, it is covered in rust and weighs 14g. CLAIM: The rusting of the nail is a chemical change. Which piece of EVIDENCE best supports this claim?", a: "The iron changed into an entirely new orange-brown substance with different properties.", options: ["The iron changed into a new orange-brown substance with different properties.", "The nail was left outside for two weeks.", "The nail became heavier because it got wet.", "The nail can be cleaned with a piece of sandpaper."], correct: 0, type: "single" },
        { q: "A student conducts a reaction between 5g of baking soda and 20g of vinegar in a 25g sealed bag. Based on the law of conservation of mass, which statement is true?", a: "The mass remained constant because it took place in a closed system, and no atoms were created or destroyed.", options: ["The mass remained constant because the reaction took place in a closed system, and no atoms were created or destroyed.", "The mass decreased because the liquid turned into a gas, which weighs less than a solid.", "The mass increased because the gas occupied more space inside the bag than the original reactants.", "The mass remained constant because the experiment involved a physical change rather than a chemical reaction."], correct: 0, type: "single" },
        { q: "CER Scenario: Vinegar and baking soda react in a sealed bag. The bag puffs up with gas, but the scale reading stays the same. Which REASONING correctly connects this to the Law of Conservation of Mass?", a: "The mass stayed the same because atoms were rearranged into new molecules, but none were lost.", options: ["The mass stayed the same because atoms were rearranged into new molecules, but none were lost.", "The mass stayed the same because gas has no weight.", "The mass stayed the same because the reaction was physical.", "The mass stayed the same because the bag was too small to notice a change."], correct: 0, type: "single" }
    ];

    // NAVIGATION VARIABLES
    let currentQuizIdx = 0;
    let quizScore = 0;
    let currentCardIdx = 0;

    // VIEW SWITCHER ENGINE
    function switchView(viewId) {
        document.querySelectorAll('.view-panel, #menu-view').forEach(panel => panel.style.display = 'none');
        document.getElementById(viewId).style.display = (viewId === 'menu-view') ? 'grid' : 'block';
        if(viewId === 'flashcard-view') {
            document.getElementById('flashcard').classList.remove('flipped');
            loadCard();
        }
    }

    // GENERATE QUIZ CONTENT DYNAMICALLY
    function buildQuiz() {
        const container = document.getElementById('questions-container');
        container.innerHTML = "";
        coreData.forEach((item, qIdx) => {
            const qBox = document.createElement('div');
            qBox.className = `question-box ${qIdx === 0 ? 'active' : ''}`;
            qBox.setAttribute('data-type', item.type);
            if (item.type === 'single') qBox.setAttribute('data-correct', item.correct);
            else qBox.setAttribute('data-correct-indices', item.correctIndices.join(','));

            let optionsHTML = '';
            item.options.forEach((opt, oIdx) => {
                if(item.type === 'single') {
                    optionsHTML += `<li class="option-item" onclick="checkSingle(this, ${oIdx}, ${qIdx})">${opt}</li>`;
                } else {
                    optionsHTML += `<li class="option-item" onclick="toggleMulti(this)">${opt}</li>`;
                }
            });

            qBox.innerHTML = `
                <div class="question-text">${item.q}</div>
                ${item.type === 'multi' ? '<span class="multi-info">(Choose TWO options, then click Next)</span>' : ''}
                <ul class="options-list">${optionsHTML}</ul>
            `;
            container.appendChild(qBox);
        });
    }

    // QUIZ ENGINE LOGIC
    function navigateQuiz(dir) {
        const boxes = document.querySelectorAll('.question-box');
        const currentBox = boxes[currentQuizIdx];

        if(dir === 1 && currentBox.getAttribute('data-type') === 'multi' && !currentBox.classList.contains('processed')) {
            evaluateMulti(currentBox);
        }

        if(dir === 1 && currentQuizIdx === boxes.length - 1) {
            showScore();
            return;
        }

        boxes[currentQuizIdx].classList.remove('active');
        currentQuizIdx += dir;
        boxes[currentQuizIdx].classList.add('active');
        
        document.getElementById('quiz-progress').innerText = `Question ${currentQuizIdx + 1} of ${boxes.length}`;
        document.getElementById('quizPrev').disabled = currentQuizIdx === 0;
        document.getElementById('quizNext').innerText = (currentQuizIdx === boxes.length - 1) ? "Finish" : "Next";
    }

    function checkSingle(element, chosenIdx, qIdx) {
        const box = element.closest('.question-box');
        if(box.classList.contains('answered')) return;

        const correctIdx = coreData[qIdx].correct;
        const options = box.querySelectorAll('.option-item');

        if(chosenIdx === correctIdx) {
            element.classList.add('correct');
            quizScore++;
        } else {
            element.classList.add('wrong');
            options[correctIdx].classList.add('correct');
        }
        box.classList.add('answered');
    }

    function toggleMulti(element) {
        const box = element.closest('.question-box');
        if(box.classList.contains('processed')) return;
        element.classList.toggle('wrong'); // Visual styling state toggle
    }

    function evaluateMulti(box) {
        const correctIndices = box.getAttribute('data-correct-indices').split(',').map(Number);
        const options = box.querySelectorAll('.option-item');
        let selected = [];

        options.forEach((opt, idx) => {
            if(opt.classList.contains('wrong')) {
                selected.push(idx);
                opt.classList.remove('wrong');
            }
        });

        let isCorrect = selected.length === correctIndices.length && selected.every(v => correctIndices.includes(v));
        options.forEach((opt, idx) => {
            if(correctIndices.includes(idx)) opt.classList.add('correct');
            else if(selected.includes(idx)) opt.classList.add('wrong');
        });

        if(isCorrect) quizScore++;
        box.classList.add('processed');
    }

    function showScore() {
        document.getElementById('quiz-body').style.display = 'none';
        document.getElementById('quiz-score-screen').style.display = 'block';
        document.getElementById('final-score').innerText = quizScore;
    }

    function resetQuiz() {
        quizScore = 0;
        currentQuizIdx = 0;
        document.getElementById('quiz-body').style.display = 'block';
        document.getElementById('quiz-score-screen').style.display = 'none';
        buildQuiz();
        document.getElementById('quiz-progress').innerText = `Question 1 of ${coreData.length}`;
        document.getElementById('quizPrev').disabled = true;
        document.getElementById('quizNext').innerText = "Next";
    }

    // FLASHCARD ENGINE LOGIC
    function flipCard() {
        document.getElementById('flashcard').classList.toggle('flipped');
    }

    function loadCard() {
        document.getElementById('front-text').innerText = coreData[currentCardIdx].q;
        document.getElementById('back-text').innerHTML = coreData[currentCardIdx].a.replace(/\n/g, '<br>');
        document.getElementById('card-counter').innerText = `Card ${currentCardIdx + 1} of ${coreData.length}`;
    }

    function changeCard(dir) {
        document.getElementById('flashcard').classList.remove('flipped');
        setTimeout(() => {
            currentCardIdx += dir;
            if(currentCardIdx >= coreData.length) currentCardIdx = 0;
            if(currentCardIdx < 0) currentCardIdx = coreData.length - 1;
            loadCard();
        }, 150);
    }

    // Initialize Page
    buildQuiz();
</script>

</body>
</html>
