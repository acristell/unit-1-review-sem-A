<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>7th Grade Science Ultimate Review Hub</title>
    <style>
        :root {
            --primary: #3182ce;
            --primary-dark: #2b6cb0;
            --secondary: #4a5568;
            --dark: #1a202c;
            --light: #f7fafc;
            --success: #38a169;
            --danger: #e53e3e;
            --warning: #dd6b20;
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

        header h1 { margin: 0; font-size: 2.2rem; }
        header p { margin: 10px 0 0 0; opacity: 0.9; font-size: 1.1rem; }

        .container {
            max-width: 950px;
            margin: 40px auto;
            padding: 0 20px;
        }

        /* Menu Grid */
        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
            margin-top: 20px;
        }

        .menu-card {
            background: white;
            border-radius: 12px;
            padding: 25px;
            text-align: center;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
            border: 1px solid #e2e8f0;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .menu-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
            border-color: var(--primary);
        }

        .menu-card h2 { margin-top: 0; color: var(--primary-dark); font-size: 1.4rem; }
        .menu-card p { color: #718096; font-size: 0.95rem; line-height: 1.5; margin-bottom: 20px; }

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
            display: inline-block;
        }

        .main-btn:hover { background-color: var(--primary-dark); }

        /* Workspace Panels */
        .view-panel {
            display: none;
            background: white;
            border-radius: 12px;
            padding: 30px;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
            animation: fadeIn 0.4s ease;
        }

        .back-bar { display: flex; justify-content: flex-start; margin-bottom: 20px; }
        .back-btn {
            background-color: #e2e8f0; color: var(--dark); border: none;
            padding: 8px 16px; font-weight: 600; border-radius: 6px; cursor: pointer;
        }
        .back-btn:hover { background-color: #cbd5e0; }

        /* --- QUIZ STYLES --- */
        .question-box { display: none; }
        .question-box.active { display: block; }
        .question-text { font-size: 1.2rem; font-weight: 600; margin-bottom: 20px; line-height: 1.5; }
        .options-list { list-style: none; padding: 0; }
        .option-item {
            background: var(--light); border: 2px solid #e2e8f0; border-radius: 8px;
            padding: 14px; margin-bottom: 12px; cursor: pointer; font-weight: 500; transition: all 0.2s;
        }
        .option-item:hover { border-color: var(--primary); background: #ebf8ff; }
        .option-item.correct { background-color: #c6f6d5 !important; border-color: var(--success) !important; color: #22543d; font-weight: bold; }
        .option-item.wrong { background-color: #fed7d7 !important; border-color: var(--danger) !important; color: #742a2a; }
        .quiz-controls { display: flex; justify-content: space-between; margin-top: 25px; }
        .progress-text { font-weight: bold; color: #718096; margin-bottom: 15px; text-align: right; }
        .multi-info { font-style: italic; color: var(--warning); font-weight: bold; display: block; margin-bottom: 10px; }

        /* --- FLASHCARD STYLES --- */
        .flashcard-wrapper { max-width: 550px; margin: 0 auto; perspective: 1000px; }
        .card-container {
            width: 100%; height: 300px; position: relative;
            transform-style: preserve-3d; transition: transform 0.5s ease; cursor: pointer;
        }
        .card-container.flipped { transform: rotateY(180deg); }
        .card-side {
            position: absolute; width: 100%; height: 100%; backface-visibility: hidden;
            display: flex; align-items: center; justify-content: center; border-radius: 15px;
            box-shadow: 0 6px 15px rgba(0,0,0,0.1); padding: 30px; font-size: 1.25rem;
            box-sizing: border-box; text-align: center; line-height: 1.5;
        }
        .card-front { background: linear-gradient(135deg, var(--primary), var(--primary-dark)); color: white; }
        .card-back { background: white; color: var(--dark); transform: rotateY(180deg); border: 3px dashed var(--primary); }
        .card-controls { display: flex; justify-content: space-around; align-items: center; margin-top: 30px; }
        .hint { position: absolute; bottom: 15px; font-size: 0.8rem; opacity: 0.8; letter-spacing: 1px; }

        /* --- PH SCALER STYLES --- */
        .ph-scale-track {
            display: flex; height: 50px; border-radius: 8px; margin: 30px 0;
            overflow: hidden; box-shadow: inset 0 2px 4px rgba(0,0,0,0.2);
        }
        .ph-node {
            flex: 1; display: flex; align-items: center; justify-content: center;
            color: white; font-weight: bold; cursor: pointer; transition: transform 0.2s;
        }
        .ph-node:hover { transform: scale(1.05); z-index: 2; }
        .game-card-display {
            background: var(--light); border: 2px solid #cbd5e0; padding: 20px;
            border-radius: 8px; text-align: center; font-size: 1.3rem; font-weight: bold; margin-bottom: 20px;
        }

        /* --- LAB SIMULATOR STYLES --- */
        .lab-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; margin-top: 20px; }
        .lab-station {
            border: 2px solid #e2e8f0; border-radius: 10px; padding: 20px; text-align: center;
            background: var(--light); cursor: pointer; transition: all 0.2s;
        }
        .lab-station:hover { border-color: var(--primary); background: #fff; }
        .lab-station.active { border-color: var(--warning); background: #fffaf0; box-shadow: 0 0 10px rgba(221,107,32,0.2); }
        .mini-stage { height: 100px; display: flex; align-items: center; justify-content: center; font-size: 3rem; margin-bottom: 10px; }
        .sim-controls { margin-top: 25px; padding: 20px; border-top: 2px solid #e2e8f0; display: none; text-align: center;}
        .sim-feedback { font-weight: bold; margin-top: 15px; font-size: 1.1rem; }

        /* --- SORTING MATRIX STYLES --- */
        .matrix-buckets { display: grid; grid-template-columns: repeat(3, 1fr); gap: 15px; margin-top: 25px; }
        .matrix-bucket {
            border: 2px dashed #cbd5e0; border-radius: 10px; min-height: 120px;
            display: flex; flex-direction: column; align-items: center; justify-content: center;
            background: var(--light); font-weight: bold; transition: background 0.2s;
        }
        .matrix-bucket:hover { background: #ebf8ff; border-color: var(--primary); }

        /* --- MASS BALANCER STYLES --- */
        .scale-arena { display: flex; align-items: center; justify-content: center; margin: 40px 0; }
        .scale-beam {
            width: 400px; height: 10px; background: #718096; position: relative;
            display: flex; justify-content: space-between; transition: transform 0.5s ease;
        }
        .scale-fulcrum {
            width: 0; height: 0; border-left: 20px solid transparent; border-right: 20px solid transparent;
            border-bottom: 30px solid #4a5568; margin: 0 auto; position: relative; top: -2px; z-index: -1;
        }
        .scale-pan {
            width: 100px; height: 20px; background: #a0aec0; border-radius: 0 0 50px 50px;
            position: absolute; top: 10px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        .pan-left { left: -30px; } .pan-right { right: -30px; }
        .pan-content { position: absolute; bottom: 20px; width: 100%; text-align: center; font-size: 1.8rem; }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

<header>
    <h1>7th Grade Physical Science Review Hub</h1>
    <p>Master Matter, Elements, Compounds, Mixtures, pH, & Chemical Changes</p>
</header>

<div class="container">

    <div id="menu-view" class="menu-grid">
        <div class="menu-card" onclick="switchView('quiz-view')">
            <h2>📝 Interactive Quiz</h2>
            <p>Test your knowledge with an interactive 20-question comprehensive unit review. Get instant scoring!</p>
            <button class="main-btn">Start Quiz</button>
        </div>

        <div class="menu-card" onclick="switchView('flashcard-view')">
            <h2>🎴 Study Flashcards</h2>
            <p>Review key definitions, pH thresholds, and core system laws at your own pace with responsive flipping cards.</p>
            <button class="main-btn">Open Cards</button>
        </div>

        <div class="menu-card" onclick="switchView('ph-scaler-view')">
            <h2>🎚️ pH Scaler Game</h2>
            <p>Analyze household items and locate them correctly along the colorful acidic/basic spectrum map.</p>
            <button class="main-btn">Play Game</button>
        </div>

        <div class="menu-card" onclick="switchView('lab-simulator-view')">
            <h2>🧪 Lab Simulator</h2>
            <p>Trigger live virtual experiments at 4 testing stations and identify physical versus chemical reactions.</p>
            <button class="main-btn">Enter Lab</button>
        </div>

        <div class="menu-card" onclick="switchView('sorting-matrix-view')">
            <h2>🧩 Matter Sorting Matrix</h2>
            <p>Categorize random substance targets cleanly into Elements, Compounds, or Mixtures columns.</p>
            <button class="main-btn">Sort Matter</button>
        </div>

        <div class="menu-card" onclick="switchView('mass-balancer-view')">
            <h2>⚖️ Mass Balancer</h2>
            <p>React chemical systems inside a sealed vessel and solve weights using the Law of Conservation of Mass.</p>
            <button class="main-btn">Balance Scale</button>
        </div>
    </div>

    <div id="quiz-view" class="view-panel">
        <div class="back-bar"><button class="back-btn" onclick="switchView('menu-view')">⬅ Main Menu</button></div>
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
        <div class="back-bar"><button class="back-btn" onclick="switchView('menu-view')">⬅ Main Menu</button></div>
        <div class="flashcard-wrapper">
            <div class="card-container" id="flashcard" onclick="flipCard()">
                <div class="card-side card-front"><span id="front-text">Loading...</span><div class="hint">CLICK TO FLIP</div></div>
                <div class="card-side card-back"><span id="back-text">Loading...</span><div class="hint" style="color:#718096;">CLICK TO FLIP BACK</div></div>
            </div>
            <div class="card-controls">
                <button class="main-btn" onclick="changeCard(-1)">⬅ Prev</button>
                <span id="card-counter" style="font-weight:bold; color:var(--secondary);">Card 1 of 20</span>
                <button class="main-btn" onclick="changeCard(1)">Next ➡</button>
            </div>
        </div>
    </div>

    <div id="ph-scaler-view" class="view-panel">
        <div class="back-bar"><button class="back-btn" onclick="switchView('menu-view')">⬅ Main Menu</button></div>
        <h2>🎚️ pH Spectrum Scaler</h2>
        <p>Analyze the household item card below, then click the correct number box on the pH scale timeline!</p>
        <div class="game-card-display" id="ph-item-target">Target Item</div>
        <div class="ph-scale-track" id="ph-track-element"></div>
        <div id="ph-game-feedback" style="font-weight:bold; text-align:center; font-size:1.2rem; margin-top:15px;"></div>
    </div>

    <div id="lab-simulator-view" class="view-panel">
        <div class="back-bar"><button class="back-btn" onclick="switchView('menu-view')">⬅ Main Menu</button></div>
        <h2>🧪 Lab Simulation Bench</h2>
        <p>Select a testing lab station below to trigger an environmental change reaction experiment:</p>
        <div class="lab-grid">
            <div class="lab-station" onclick="runLabStation(0)" id="station-0"><div class="mini-stage" id="stage-0">🧊</div><h3>Station 1</h3><p>Ice Cylinder</p></div>
            <div class="lab-station" onclick="runLabStation(1)" id="station-1"><div class="mini-stage" id="stage-1">🪵</div><h3>Station 2</h3><p>Wood Block</p></div>
            <div class="lab-station" onclick="runLabStation(2)" id="station-2"><div class="mini-stage" id="stage-2">🧪</div><h3>Station 3</h3><p>Clear Liquids Mixture</p></div>
            <div class="lab-station" onclick="runLabStation(3)" id="station-3"><div class="mini-stage" id="stage-3">🔩</div><h3>Station 4</h3><p>Iron Beam Setup</p></div>
        </div>
        <div class="sim-controls" id="lab-sim-controls">
            <h3 id="sim-title">Station Task</h3>
            <p style="font-weight:bold;">Classify this transformation change:</p>
            <button class="main-btn" style="background-color:var(--primary);" onclick="answerLabType('Physical')">Physical Change</button>
            <button class="main-btn" style="background-color:var(--warning);" onclick="answerLabType('Chemical')">Chemical Change</button>
            <div class="sim-feedback" id="lab-feedback"></div>
        </div>
    </div>

    <div id="sorting-matrix-view" class="view-panel">
        <div class="back-bar"><button class="back-btn" onclick="switchView('menu-view')">⬅ Main Menu</button></div>
        <h2>🧩 Matter Sorting Matrix</h2>
        <p>Route the target substance below into its absolute structural classification basket column:</p>
        <div class="game-card-display" id="matrix-item-target">Loading item...</div>
        <div style="text-align:center; margin-bottom:20px;">
            <button class="main-btn" onclick="sortMatrixAction('Element')">Element</button>
            <button class="main-btn" style="background-color:var(--secondary);" onclick="sortMatrixAction('Compound')">Compound</button>
            <button class="main-btn" style="background-color:var(--warning);" onclick="sortMatrixAction('Mixture')">Mixture</button>
        </div>
        <div class="matrix-buckets">
            <div class="matrix-bucket" id="bucket-Element">Elements Collection</div>
            <div class="matrix-bucket" id="bucket-Compound">Compounds Collection</div>
            <div class="matrix-bucket" id="bucket-Mixture">Mixtures Collection</div>
        </div>
        <div id="matrix-feedback" style="font-weight:bold; text-align:center; font-size:1.2rem; margin-top:20px;"></div>
    </div>

    <div id="mass-balancer-view" class="view-panel">
        <div class="back-bar"><button class="back-btn" onclick="switchView('menu-view')">⬅ Main Menu</button></div>
        <h2>⚖️ Mass Balancer System</h2>
        <p>A closed vessel system seals 5 grams of Baking Soda combined with 20 grams of Vinegar inside. Click React to run the system:</p>
        <div style="text-align:center;"><button class="main-btn" id="react-btn" onclick="triggerMassReaction()">React System! 🧪</button></div>
        <div class="scale-arena">
            <div class="scale-beam" id="balance-beam">
                <div class="scale-pan pan-left"><div class="pan-content" id="left-pan-icon">🛍️</div></div>
                <div class="scale-pan pan-right"><div class="pan-content" id="right-pan-icon">❓</div></div>
            </div>
        </div>
        <div class="scale-fulcrum"></div>
        <div id="balancer-options" style="text-align:center; margin-top:20px; display:none;">
            <p style="font-weight:bold;">Choose the exact balance counterweight to level the balancing beam:</p>
            <button class="main-btn" onclick="guessMassWeight(20)">Apply 20g Counterweight</button>
            <button class="main-btn" onclick="guessMassWeight(25)">Apply 25g Counterweight</button>
            <button class="main-btn" onclick="guessMassWeight(30)">Apply 30g Counterweight</button>
        </div>
        <div id="balancer-feedback" style="font-weight:bold; text-align:center; font-size:1.1rem; margin-top:20px; padding:0 15px; line-height:1.4;"></div>
    </div>

</div>

<script>
    // CORE ASSESSMENT SYSTEM DATA SOURCE
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

    // CONTROL POINTER TRACKERS
    let currentQuizIdx = 0, quizScore = 0, currentCardIdx = 0;

    // VIEW ROUTING ENGINE
    function switchView(viewId) {
        document.querySelectorAll('.view-panel, #menu-view').forEach(p => p.style.display = 'none');
        document.getElementById(viewId).style.display = (viewId === 'menu-view') ? 'grid' : 'block';
        if(viewId === 'flashcard-view') { document.getElementById('flashcard').classList.remove('flipped'); loadCard(); }
        if(viewId === 'ph-scaler-view') initPhGame();
        if(viewId === 'sorting-matrix-view') initMatrixGame();
        if(viewId === 'lab-simulator-view') initLabSim();
        if(viewId === 'mass-balancer-view') initMassBalancer();
    }

    // --- QUIZ GAME SUBSYSTEM ---
    function buildQuiz() {
        const container = document.getElementById('questions-container'); container.innerHTML = "";
        coreData.forEach((item, qIdx) => {
            const qBox = document.createElement('div');
            qBox.className = `question-box ${qIdx === 0 ? 'active' : ''}`;
            qBox.setAttribute('data-type', item.type);
            qBox.setAttribute(item.type === 'single' ? 'data-correct' : 'data-correct-indices', item.type === 'single' ? item.correct : item.correctIndices.join(','));
            let opts = '';
            item.options.forEach((opt, oIdx) => {
                opts += `<li class="option-item" onclick="${item.type === 'single' ? `checkSingle(this, ${oIdx}, ${qIdx})` : 'toggleMulti(this)'}">${opt}</li>`;
            });
            qBox.innerHTML = `<div class="question-text">${item.q}</div>${item.type === 'multi' ? '<span class="multi-info">(Choose TWO options, then click Next)</span>' : ''}<ul class="options-list">${opts}</ul>`;
            container.appendChild(qBox);
        });
    }
    function navigateQuiz(dir) {
        const boxes = document.querySelectorAll('.question-box'); const currentBox = boxes[currentQuizIdx];
        if(dir === 1 && currentBox.getAttribute('data-type') === 'multi' && !currentBox.classList.contains('processed')) evaluateMulti(currentBox);
        if(dir === 1 && currentQuizIdx === boxes.length - 1) { showScore(); return; }
        boxes[currentQuizIdx].classList.remove('active'); currentQuizIdx += dir; boxes[currentQuizIdx].classList.add('active');
        document.getElementById('quiz-progress').innerText = `Question ${currentQuizIdx + 1} of ${boxes.length}`;
        document.getElementById('quizPrev').disabled = currentQuizIdx === 0;
        document.getElementById('quizNext').innerText = (currentQuizIdx === boxes.length - 1) ? "Finish" : "Next";
    }
    function checkSingle(element, chosenIdx, qIdx) {
        const box = element.closest('.question-box'); if(box.classList.contains('answered')) return;
        const correctIdx = coreData[qIdx].correct; const options = box.querySelectorAll('.option-item');
        if(chosenIdx === correctIdx) { element.classList.add('correct'); quizScore++; } else { element.classList.add('wrong'); options[correctIdx].classList.add('correct'); }
        box.classList.add('answered');
    }
    function toggleMulti(element) {
        const box = element.closest('.question-box'); if(box.classList.contains('processed')) return;
        element.classList.toggle('wrong');
    }
    function evaluateMulti(box) {
        const correctIndices = box.getAttribute('data-correct-indices').split(',').map(Number); const options = box.querySelectorAll('.option-item');
        let selected = []; options.forEach((opt, idx) => { if(opt.classList.contains('wrong')) { selected.push(idx); opt.classList.remove('wrong'); } });
        let isCorrect = selected.length === correctIndices.length && selected.every(v => correctIndices.includes(v));
        options.forEach((opt, idx) => { if(correctIndices.includes(idx)) opt.classList.add('correct'); else if(selected.includes(idx)) opt.classList.add('wrong'); });
        if(isCorrect) quizScore++; box.classList.add('processed');
    }
    function showScore() { document.getElementById('quiz-body').style.display = 'none'; document.getElementById('quiz-score-screen').style.display = 'block'; document.getElementById('final-score').innerText = quizScore; }
    function resetQuiz() { quizScore = 0; currentQuizIdx = 0; document.getElementById('quiz-body').style.display = 'block'; document.getElementById('quiz-score-screen').style.display = 'none'; buildQuiz(); document.getElementById('quizPrev').disabled = true; document.getElementById('quizNext').innerText = "Next"; }

    // --- FLASHCARD SUBSYSTEM ---
    function flipCard() { document.getElementById('flashcard').classList.toggle('flipped'); }
    function loadCard() { frontEl.innerText = coreData[currentCardIdx].q; backEl.innerHTML = coreData[currentCardIdx].a.replace(/\n/g, '<br>'); counterEl.innerText = `Card ${currentCardIdx + 1} of ${coreData.length}`; }
    function changeCard(dir) { document.getElementById('flashcard').classList.remove('flipped'); setTimeout(() => { currentCardIdx += dir; if(currentCardIdx >= coreData.length) currentCardIdx = 0; if(currentCardIdx < 0) currentCardIdx = coreData.length - 1; loadCard(); }, 150); }

    // --- GAME 1: pH SCALER SYSTEM ---
    const phData = [
        { name: "Lemon Juice", val: 2, type: "Strong Acid" },
        { name: "Whole Milk", val: 6, type: "Weak Acid" },
        { name: "Household Soap", val: 10, type: "Weak Base" },
        { name: "Industrial Bleach", val: 13, type: "Strong Base" }
    ];
    let currentPhIdx = 0;
    function initPhGame() {
        currentPhIdx = 0; document.getElementById('ph-game-feedback').innerText = "";
        const track = document.getElementById('ph-track-element'); track.innerHTML = "";
        const hexColors = ["#ef4444", "#f97316", "#f59e0b", "#eab308", "#84cc16", "#22c55e", "#10b981", "#059669", "#06b6d4", "#06b6d4", "#3b82f6", "#1d4ed8", "#4338ca", "#581c87", "#4c1d95"];
        for(let i=0; i<=14; i++) {
            const node = document.createElement('div'); node.className = "ph-node";
            node.innerText = i; node.style.backgroundColor = hexColors[i];
            node.onclick = () => guessPhValue(i); track.appendChild(node);
        }
        loadPhTarget();
    }
    function loadPhTarget() {
        if(currentPhIdx >= phData.length) { document.getElementById('ph-item-target').innerText = "Spectrum Cleared! 🎉"; return; }
        document.getElementById('ph-item-target').innerText = `Where does "${phData[currentPhIdx].name}" belong on the pH Scale?`;
    }
    function guessPhValue(num) {
        if(currentPhIdx >= phData.length) return;
        const target = phData[currentPhIdx]; const feedback = document.getElementById('ph-game-feedback');
        if(num === target.val) {
            feedback.innerHTML = `<span style="color:var(--success)">Correct! ${target.name} has a pH of ${target.val} (${target.type}).</span>`;
            currentPhIdx++; setTimeout(() => { feedback.innerText = ""; loadPhTarget(); }, 2000);
        } else {
            feedback.innerHTML = `<span style="color:var(--danger)">Not quite. Try matching ${target.name} again! Hint: Look carefully at its classification numbers.</span>`;
        }
    }

    // --- GAME 2: LAB SIMULATOR SYSTEM ---
    const labStations = [
        { title: "Station 1: Cylinder Thermal Test", original: "🧊", react: "💧", type: "Physical", info: "Correct! The ice undergoes a phase change state transformation into liquid water, but remains structurally H₂O." },
        { title: "Station 2: Combustion Chamber Setup", original: "🪵", react: "💨🌋", type: "Chemical", info: "Correct! Wood burning breaks original atomic bonds and creates an entirely new chemical structure configuration (ash/smoke)." },
        { title: "Station 3: Aqueous Mixing Task", original: "🧪🧪", react: "🫧⚡", type: "Chemical", info: "Correct! Mixing separate transparent liquids causes violent bubbling gas releases and precipitations." },
        { title: "Station 4: Long-Term Oxidation Setup", original: "🔩", react: "🪛🟠", type: "Chemical", info: "Correct! Rust transformation formulas bind oxygen onto base iron creating completely distinct properties." }
    ];
    let selectedStationIdx = null;
    function initLabSim() {
        selectedStationIdx = null; document.getElementById('lab-sim-controls').style.display = "none";
        document.getElementById('lab-feedback').innerText = "";
        for(let i=0; i<4; i++) { document.getElementById(`station-${i}`).classList.remove('active'); document.getElementById(`stage-${i}`).innerText = labStations[i].original; }
    }
    function runLabStation(idx) {
        initLabSim(); selectedStationIdx = idx;
        document.getElementById(`station-${idx}`).classList.add('active');
        document.getElementById(`stage-${idx}`).innerText = labStations[idx].react;
        document.getElementById('sim-title').innerText = labStations[idx].title;
        document.getElementById('lab-sim-controls').style.display = "block";
    }
    function answerLabType(type) {
        if(selectedStationIdx === null) return;
        const currentStation = labStations[selectedStationIdx];
        const fb = document.getElementById('lab-feedback');
        if(type === currentStation.type) { fb.innerHTML = `<span style="color:var(--success)">${currentStation.info}</span>`; }
        else { fb.innerHTML = `<span style="color:var(--danger)">Incorrect classification. Observe the products carefully to verify if unique compounds formed!</span>`; }
    }

    // --- GAME 3: MATTER MATRIX SYSTEM ---
    const matrixData = [
        { name: "Pure Gold Bar (Au)", type: "Element" },
        { name: "Pure Oxygen Gas (O₂)", type: "Element" },
        { name: "Table Salt Compound (NaCl)", type: "Compound" },
        { name: "Water Molecule System (H₂O)", type: "Compound" },
        { name: "Salt and Pepper Tossing Bowl Mixture", type: "Mixture" },
        { name: "Evaporation Puddle Solid Mix", type: "Mixture" }
    ];
    let currentMatrixIdx = 0;
    function initMatrixGame() {
        currentMatrixIdx = 0; document.getElementById('matrix-feedback').innerText = "";
        document.getElementById('bucket-Element').innerHTML = "<b>Elements Collection</b>";
        document.getElementById('bucket-Compound').innerHTML = "<b>Compounds Collection</b>";
        document.getElementById('bucket-Mixture').innerHTML = "<b>Mixtures Collection</b>";
        loadMatrixTarget();
    }
    function loadMatrixTarget() {
        if(currentMatrixIdx >= matrixData.length) { document.getElementById('matrix-item-target').innerText = "Matrix Baskets Full! 🏆"; return; }
        document.getElementById('matrix-item-target').innerText = matrixData[currentMatrixIdx].name;
    }
    function sortMatrixAction(category) {
        if(currentMatrixIdx >= matrixData.length) return;
        const currentTarget = matrixData[currentMatrixIdx]; const fb = document.getElementById('matrix-feedback');
        if(category === currentTarget.type) {
            fb.innerHTML = `<span style="color:var(--success)">Correct Sorting!</span>`;
            const bucket = document.getElementById(`bucket-${category}`);
            bucket.innerHTML += `<div style="font-size:0.85rem; background:#fff; padding:3px; margin:3px; border-radius:4px; box-shadow:0 1px 2px rgba(0,0,0,0.1);">${currentTarget.name}</div>`;
            currentMatrixIdx++; setTimeout(() => { fb.innerText = ""; loadMatrixTarget(); }, 1200);
        } else {
            fb.innerHTML = `<span style="color:var(--danger)">Incorrect basket assignment. Review the atomic structure behavior configuration rules.</span>`;
        }
    }

    // --- GAME 4: MASS BALANCER SYSTEM ---
    function initMassBalancer() {
        document.getElementById('balance-beam').style.transform = "rotate(0deg)";
        document.getElementById('left-pan-icon').innerText = "🛍️ (25g)";
        document.getElementById('right-pan-icon').innerText = "❓";
        document.getElementById('react-btn').disabled = false;
        document.getElementById('balancer-options').style.display = "none";
        document.getElementById('balancer-feedback').innerText = "";
    }
    function triggerMassReaction() {
        document.getElementById('left-pan-icon').innerText = "🎈💨";
        document.getElementById('balance-beam').style.transform = "rotate(-8deg)";
        document.getElementById('react-btn').disabled = true;
        document.getElementById('balancer-options').style.display = "block";
        document.getElementById('balancer-feedback').innerHTML = "The chemical reaction generated high pressure gases inside the sealed bag. The beam tilted due to unbalanced weights!";
    }
    function guessMassWeight(val) {
        const fb = document.getElementById('balancer-feedback');
        if(val === 25) {
            document.getElementById('balance-beam').style.transform = "rotate(0deg)";
            document.getElementById('right-pan-icon').innerText = "⚖️ (25g)";
            fb.innerHTML = `<span style="color:var(--success)"><b>Perfect Balance! 🌟</b><br>The Law of Conservation of Mass dictates that atoms are never destroyed or created during chemical interactions. Because the tracking process ran in a closed container, the product mass equals the original reactants precisely (5g + 20g = 25g).</span>`;
        } else {
            fb.innerHTML = `<span style="color:var(--danger)">Incorrect selection weight. Remember that forming gaseous phases inside a closed system cannot escape or alter the total count of atoms! Try a different counterweight.</span>`;
        }
    }

    // PAGE LOAD INITIALIZATION DECLARATIONS
    const frontEl = document.getElementById('front-text');
    const backEl = document.getElementById('back-text');
    const counterEl = document.getElementById('card-counter');
    buildQuiz();
</script>

</body>
</html>
</html>
