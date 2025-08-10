<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Generatore FEROMANIA</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #0d1117;
            color: #c9d1d9;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            gap: 20px;
            grid-template-columns: 1fr 1fr;
        }
        .section {
            background-color: #161b22;
            border: 1px solid #30363d;
            border-radius: 8px;
            padding: 20px;
        }
        h1, h2, h4 {
            text-align: center;
            color: #58a6ff;
            text-shadow: 0 0 5px #58a6ff;
        }
        select, input[type="text"] {
            width: calc(100% - 22px);
            padding: 10px;
            margin-bottom: 10px;
            background-color: #0d1117;
            color: #c9d1d9;
            border: 1px solid #30363d;
            border-radius: 4px;
        }
        button {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            background-color: #58a6ff;
            color: #0d1117;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
        }
        button:hover {
            background-color: #79c0ff;
        }
        .result-box {
            background-color: #0d1117;
            border: 1px solid #30363d;
            border-radius: 4px;
            padding: 15px;
            min-height: 200px;
        }
        .result-box h3 {
            color: #8b949e;
            margin-top: 0;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 10px;
            font-family: 'Courier New', Courier, monospace;
        }
        th, td {
            border: 1px solid #30363d;
            padding: 8px;
            text-align: left;
        }
        th {
            background-color: #21262d;
            color: #58a6ff;
        }
        .info-card {
            background-color: #21262d;
            border-left: 3px solid #58a6ff;
            padding: 10px;
            margin-bottom: 10px;
        }
        @media (max-width: 768px) {
            .container {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <h1>Generatore FEROMANIA</h1>
    <div class="container">
        <div class="section">
            <h2>Genera PNG</h2>
            <div class="info-card">
                Scegli specie, nome e specialità per generare un PNG completo.
            </div>
            <select id="png-species">
                <option value="">-- Seleziona Specie --</option>
                <option value="Coleotteri">Coleotteri</option>
                <option value="Ditteri">Ditteri</option>
                <option value="Forminidi">Forminidi</option>
                <option value="Lepidotteri">Lepidotteri</option>
                <option value="Mantidi">Mantidi</option>
                <option value="Ortotteri">Ortotteri</option>
                <option value="Siringhi">Siringhi</option>
                <option value="Vespidi">Vespidi</option>
            </select>
            <select id="png-name">
                <option value="">-- Seleziona Nome --</option>
            </select>
            <select id="png-specialita">
                <option value="">-- Seleziona Specialità --</option>
                <option value="Alchimista">Alchimista</option>
                <option value="Assassino">Assassino</option>
                <option value="Cyborg">Cyborg</option>
                <option value="Guerriero">Guerriero</option>
                <option value="Medico">Medico</option>
                <option value="Mercante">Mercante</option>
                <option value="Sciamano">Sciamano</option>
                <option value="Tecnico">Tecnico</option>
            </select>
            <button id="generate-png">Genera PNG</button>
            <div id="png-result" class="result-box">
                <h3>Risultato PNG:</h3>
            </div>
        </div>

        <div class="section">
            <h2>Genera Aberrazione</h2>
            <div class="info-card">
                Scegli nome, specie, stato e livello per creare un'aberrazione unica.
            </div>
            <input type="text" id="ab-name" placeholder="Nome Aberrazione">
            <select id="ab-species">
                <option value="">-- Seleziona Specie --</option>
                <option value="Ranidi">Ranidi</option>
                <option value="Aracnidi">Aracnidi</option>
                <option value="Carapaci">Carapaci</option>
                <option value="Chilopodi">Chilopodi</option>
            </select>
            <select id="ab-state">
                <option value="">-- Seleziona Stato --</option>
                <option value="Tecnologica">Aberrazione Tecnologica</option>
                <option value="Putrida">Aberrazione Putrida</option>
                <option value="Primitiva">Aberrazione Primitiva</option>
                <option value="Evoluta">Aberrazione Evoluta</option>
            </select>
            <select id="ab-level">
                <option value="">-- Seleziona Livello --</option>
                <option value="Basso">Basso</option>
                <option value="Medio">Medio</option>
                <option value="Alto">Alto</option>
            </select>
            <button id="generate-ab">Genera Aberrazione</button>
            <div id="ab-result" class="result-box">
                <h3>Risultato Aberrazione:</h3>
            </div>
        </div>
    </div>

    <script>
        const namesData = {
            "Coleotteri": {
                maschili: ["Karrus", "Brok", "Scarius", "Jaxx", "Burak", "Hektor", "Gorn", "Drakon", "Rex", "Oron", "Magnus", "Torus"],
                femminili: ["Brenna", "Syla", "Gorra", "Kyla", "Drina", "Vessa", "Lyra", "Jora", "Vyla", "Brina", "Lydda", "Nora"]
            },
            "Ditteri": {
                maschili: ["Zip", "Flik", "Buzz", "Slik", "Rikk", "Wizz", "Teyl", "Mosh", "Karr", "Krikk", "Drumm", "Flyn"],
                femminili: ["Pip", "Zara", "Tizza", "Vira", "Lyra", "Nissa", "Zilla", "Jina", "Verna", "Cora", "Trixa", "Cora"]
            },
            "Forminidi": {
                maschili: ["K’arvan", "Ter’ox", "Zynto", "Zor’ak", "Mor’vin", "Vey’lor", "Jor’an", "Gorn’ak", "Renz’ar", "Rhy’na", "Tor’ak", "Mor’an"],
                femminili: ["Lyra’ka", "Ema’ra", "Ky’ana", "Sir’na", "Korra’la", "Tey’sa", "Vey’na", "Rila’na", "Cora’la", "Lyra’la", "Zira’la", "Zara’ka"]
            },
            "Lepidotteri": {
                maschili: ["Phaelon", "Sylvin", "Lyre", "Zefyr", "Silvan", "Kael", "Lyor", "Orin", "Mirus", "Joras", "Pharis", "Rilom"],
                femminili: ["Alara", "Iridia", "Miria", "Elara", "Nyx", "Aurora", "Kyla", "Lira", "Sylvana", "Vira", "Phyla", "Orina"]
            },
            "Mantidi": {
                maschili: ["Kael", "Ren", "Vex", "Jaxx", "Lyth", "Zax", "Krix", "Karr", "Zorin", "Valerius", "Torin", "Liric"],
                femminili: ["Ryla", "Syra", "Veia", "Lyra", "Kyla", "Tyra", "Nera", "Vena", "Nora", "Rina", "Myra", "Kara"]
            },
            "Ortotteri": {
                maschili: ["Jaxx", "Krick", "Boomer", "Rikk", "Rikk", "Vex", "Kael", "Kory", "Jorik", "Torin", "Valerius", "Liric"],
                femminili: ["Piper", "Lyra", "Teyla", "Jinx", "Tyra", "Mira", "Cora", "Sira", "Nera", "Rina", "Lydda", "Lyra"]
            },
            "Siringhi": {
                maschili: ["Zyk", "Teyl", "Miron", "Karr", "Zyl", "Rix", "Lyx", "Kael", "Ren", "Zorin", "Valerius", "Liric"],
                femminili: ["Teyra", "Lilla", "Miri", "Myra", "Vira", "Cora", "Sira", "Vex", "Lyra", "Lira", "Rina", "Kara"]
            },
            "Vespidi": {
                maschili: ["Jaxen", "Zel", "Kael", "Rikk", "Vex", "Zorin", "Kory", "Jax", "Joran", "Liric", "Valerius", "Lyx"],
                femminili: ["Myra", "Vexa", "Zira", "Lyra", "Teyla", "Nora", "Rina", "Tyra", "Vena", "Kara", "Cora", "Sira"]
            }
        };
        const speciesData = {
            "Coleotteri": { caratteristiche: ["Forza", "Intelletto", "Resistenza"], peculiarita: "Prelibatezza culinaria: Quando un Coleottero ingurgita del terreno o degli sccarti vegetali o di altre creature, può eseguire una prova con caratteritica specie RESISTENZA e una caratteristica specialità a scelta tra ADATTABILITA’, BIOTECNOLOGIA e FEROCIA e per ogni successo ottenuto posticipa gli EFFETTI DI SOGGEZIONE da Simbyomax di 1 ora." },
            "Ditteri": { caratteristiche: ["Feromania", "Forza", "Agilità"], peculiarita: "Carissimo!! Quando esegue una prova ed utilizza un dado reputazione, può decidere di ritirare il dado reputazione gratuitamente." },
            "Forminidi": { caratteristiche: ["Forza", "Resistenza", "Feromania"], peculiarita: "Disciplina Ferrea: I Forminidi seguono rigorosamente ordini e gerarchie. Grazie a questa disciplina, un Forminide può aggiungere un D4 a una 'Prova Sciame', potenziando l'aiuto che offre a un alleato." },
            "Lepidotteri": { caratteristiche: ["Feromania", "Intelletto", "Agilità"], peculiarita: "Inganno feromantico: Un Lepidottero può eseguire una prova per persuadere una creatura può aggiungere un D6 alla prova, se la prova ha successo, la creatura sarà incline ad accettare le richieste del lepidottero purché siano richieste fattibili e non autolesioniste." },
            "Mantidi": { caratteristiche: ["Forza", "Agilità", "Intelletto"], peculiarita: "Primo Kata: Quando esegue un attacco da nascosto o mimetizzato, può ritirare un DADO CARATTERISTICA utilizzato nell’attacco gratuitamente." },
            "Ortotteri": { caratteristiche: ["Forza", "Agilità", "Resistenza"], peculiarita: "Verso la fuga e oltre!: grazie alle sue grandi leve, un ortottero che esegue 'l’azione fuggire' può aggiungere un D6 alla prova." },
            "Siringhi": { caratteristiche: ["Agilità", "Intelletto", "Resistenza"], peculiarita: "Va bene lo stessoo!: Un siringo ottiene gli effetti di un Simbyomax PURO anche se è SCADENTE." },
            "Vespidi": { caratteristiche: ["Feromania", "Intelletto", "Resistenza"], peculiarita: "E’ solo un ago: I vespidi possono usare i loro pungiglioni come arma, viene equipaggiata nella zona 2 dell’equipaggiamento e si attiva con caratteristica INTELLETTO e ha DADO ATTACCO D8 e l’effetto VELENO, se vine potenziato con un innesto cibernetico occupa la zona 9 degli innesti cibernetici, un armatura in quelle zone annulla l’utilizzo del pungiglione." }
        };
        const specialitaData = {
            "Alchimista": { caratteristiche: ["Biotecnologia", "Ferocia", "Mimetismo"], peculiarita: "Maestri dei Veleni: Gli Alchimisti, sono in grado di creare sostanze chimiche letali. Un Alchimista può applicare l'effetto 'CONFUSIONE' a una creatura colpita, se uno dei suoi dadi caratteristica ottiene il valore massimo.", equipaggiamento: [{ nome: "Pistola Acida", slot: "3-4", tipo: "Arma" }, { nome: "Kit Strumenti Alchemici", slot: "Inventario 1", tipo: "Equipaggiamento" }] },
            "Assassino": { caratteristiche: ["Ferocia", "Mimetismo", "Tecnologia"], peculiarita: "Dualità Violenta: Gli assassini possono scegliere di essere discreti o brutali. Un Assassino mimetizzato, una volta superato un attacco, può scegliere se infliggere danni normali e rimanere nascosto, oppure guadagnare 2 successi aggiuntivi al tiro e svelare la propria posizione a tutti gli avversari.", equipaggiamento: [{ nome: "Pugnale", slot: "3-4", tipo: "Arma" }, { nome: "Mimetica Ottica", slot: "2", tipo: "Armatura" }] },
            "Cyborg": { caratteristiche: ["Ferocia", "Adattabilità", "Tecnologia"], peculiarita: "Sostentamento Cibernetico: Gli effetti si soggezione dati dal SimByomax sono ritardati di 4h ognuno.", innesti: [{ nome: "Braccio Bionico", slot: "7-8", tipo: "Innesto" }] },
            "Guerriero": { caratteristiche: ["Adattabilità", "Ferocia", "Mimetismo"], peculiarita: "Esperienza militare: Quando un guerriero esegue un’azione di “analizzare la situazione” puo aggiungere un D6 alla prova.", equipaggiamento: [{ nome: "Manganello", slot: "3-4", tipo: "Arma" }, { nome: "Corazza", slot: "2", tipo: "Armatura" }] },
            "Medico": { caratteristiche: ["Biotecnologia", "Tecnologia", "Adattabilità"], peculiarita: "Ti salvo la vita: La specialità Medico è esperta nel campo della cura e della biotecnologia. Può declassare finno a D4 un suo dado caratteristica in BIOTECNOLOGIA, TECNOLOGIA o ADATTABILITA’, per ripristinare al massimo un dado vita suo o di un compagno anche se il compagno è attualmente senza DADI VITA.", equipaggiamento: [{ nome: "Teaser", slot: "3-4", tipo: "Arma" }, { nome: "Medikit", slot: "Inventario 1", tipo: "Equipaggiamento" }] },
            "Mercante": { caratteristiche: ["Biotecnologia", "Tecnologia", "Mimetismo"], peculiarita: "Un’offerta che non puoi rifiutare: Quando un dittero sta contrattando per un acquisto può aggiungere un D6 alla prova per convincere il compratore o venditore ad accettare la sua offerta, l’offerta deve essere comunque attendibile.", equipaggiamento: [{ nome: "Pistola", slot: "3-4", tipo: "Arma" }, { nome: "Kit Riparazione", slot: "Inventario 1", tipo: "Equipaggiamento" }] },
            "Sciamano": { caratteristiche: ["Biotecnologia", "Adattabilità", "Mimetismo"], peculiarita: "Danza Primordiale Aumentata: Un successo ottenuto con l'azione 'Danza Primordiale' conta come due successi per il calcolo degli effetti, permettendo di influenzare più nemici con un solo tiro.", equipaggiamento: [{ nome: "Asta Luminosa", slot: "3-4", tipo: "Arma" }, { nome: "Maschera Indurente", slot: "1", tipo: "Armatura" }] },
            "Tecnico": { caratteristiche: ["Adattabilità", "Tecnologia", "Mimetismo"], peculiarita: "Costi Ridotti: Il tecnico ha una comprensione innata della tecnologia. Durante la creazione di un innesto cibernetico, può scegliere se aumentare di due taglie un dado o inserire una caratteristica aggiuntiva senza pagare i costi.", equipaggiamento: [{ nome: "Pugnale Laser", slot: "3-4", tipo: "Arma" }, { nome: "Tablet", slot: "Inventario 1", tipo: "Equipaggiamento" }] }
        };
        const dicePools = [["D6", "D6", "D6"], ["D4", "D6", "D8"], ["D4", "D4", "D10"]];
        const lifeDicePools = [["D12", "D4"], ["D8", "D8"], ["D10", "D6"]];

        // Dati Aberrazioni
        const abSpeciesData = {
            "Ranidi": { caratteristiche: ["Agilità", "Feromania"], descrizione: "Queste creature, nate da rane e salamandre, hanno sviluppato una grande agilità e una sorprendente capacità di mimetismo. La loro pelle, una tela di tonalità cangianti e sfumature bioluminescenti, permette loro di fondersi con gli strati di detriti brillanti e le acque stagnanti, rendendoli praticamente invisibili fino a quando non è troppo tardi." },
            "Aracnidi": { caratteristiche: ["Forza", "Feromania"], descrizione: "Gli Aracnidi sono il risultato terrificante dell’evoluzione biochimica di un incubo primordiali. Le loro forme contorte e ingombranti nascondono una forza sproporzionata, capace di frantumare l'acciaio e sradicare interi detriti con la pura potenza muscolare." },
            "Carapaci": { caratteristiche: ["Resistenza", "Forza"], descrizione: "I Carapaci sono le fortezze viventi di Nimbius, una terrificante evoluzione di granchi e gamberi che incarna la pura, inarrestabile brutalità. Il loro corpo è avvolto in un esoscheletro impenetrabile, una corazza segmentata e massiccia che può sopportare colpi che distruggerebbero una macchina da guerra." },
            "Chilopodi": { caratteristiche: ["Agilità", "Forza"], descrizione: "I Chilopodi sono l'incubo strisciante di Nimbius, una terrificante evoluzione di centopiedi e millepiedi che si muove con una velocità e un'agilità spaventose. I loro corpi, lunghi e multi-articolati, si muovono con una frenesia innaturale che li rende una macchia quasi impossibile da seguire." }
        };
        const abStateData = {
            "Tecnologica": { caratteristiche: ["Tecnologia", "Ferocia"], descrizione: "Questa aberrazione è una fusione mostruosa tra materia organica e tecnologia malfunzionante. Innesti cibernetici sporgono dal suo corpo, emettendo scariche elettriche e luminescenze instabili." },
            "Putrida": { caratteristiche: ["Biotecnologia", "Mimetismo"], descrizione: "Questa aberrazione è il risultato di un'esposizione al Simbyomax corroso e instabile. Il suo corpo è un ammasso di carne putrida e bulbi bioluminescenti. Secreta tossine e acidi, e può camuffarsi tra i rifiuti e le rovine grazie al suo odore nauseabondo e all'aspetto sfigurato." },
            "Primitiva": { caratteristiche: ["Ferocia", "Mimetismo"], descrizione: "Questa aberrazione non ha nessuna connessione con il mondo moderno, restando ad uno stato di pura bestialità. Il suo corpo è coperto di peli o scaglie, e i suoi arti si sono trasformati in artigli e zanne." },
            "Evoluta": { caratteristiche: ["Mimetismo", "Tecnologia"], descrizione: "Questa aberrazione è un'entità ibrida, che ha sviluppato una forma di evoluzione unica, fondendo perfettamente la tecnologia con le sue capacità di mimetismo. I suoi innesti cibernetici sono perfettamente integrati e la rendono quasi impossibile da individuare." }
        };
        const abPeculiaritaData = {
            "Ranidi": "Scatto letale: Ogni volta che eseguono un’azione bonus di movimento, possono consumare la loro seconda azione bonus per eseguire un attacco ad una creatura in quella zona.",
            "Aracnidi": "Veleno Istantaneo: Gli Aracnidi hanno una Feromania unica che gli permette di iniettare un veleno estremamente potente. Quando un Aracnide effettua un attacco riuscito, il bersaglio subisce l'effetto 'Paralizzato' e ”veleno”.",
            "Carapaci": "Scudo Vivente: L'esoscheletro dei Carapaci è così resistente che funge da vera e propria corazza. I Carapaci guadagnano due successi automatici in una prova contro un attacco nemico, ma subiscono due danni aggiuntivi se l'attacco ha successo.",
            "Chilopodi": "Velocità serrante: le creature visibili al Chilopide, non possono eseguire l’azione bonus fuggire.",
            "Tecnologica": "Arma Integrata: L'aberrazione tecnologica ha armi integrate nel suo corpo. Può usare un'azione bonus per attivare un'arma cibernetica che infligge danni aggiuntivi con un dado di taglia D6 o D8.",
            "Putrida": "Nube Tossica: Tutti le azioni di attacco dell’aberrazione putrida infliggono hanno l’effetto 'ACIDO'.",
            "Primitiva": "Furia Animale: Quando un attacco di un’aberrazione primitiva fallisce, può ritirare un DADO CARATTERISTICA e accettare il nuovo risultato.",
            "Evoluta": "Mutamento Genetico: l’aberrazione evoluta può applicare sempre l’effetto 'MIMETISMO'."
        };

        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
        }
        function populateNames() {
            const speciesSelect = document.getElementById("png-species");
            const nameSelect = document.getElementById("png-name");
            const selectedSpecies = speciesSelect.value;
            nameSelect.innerHTML = "<option value=''>-- Seleziona Nome --</option>";
            if (selectedSpecies && namesData[selectedSpecies]) {
                const allNames = [...namesData[selectedSpecies].maschili, ...namesData[selectedSpecies].femminili];
                allNames.forEach(name => {
                    const option = document.createElement("option");
                    option.value = name;
                    option.textContent = name;
                    nameSelect.appendChild(option);
                });
            }
        }
        
        function generatePNG() {
            const name = document.getElementById("png-name").value;
            const species = document.getElementById("png-species").value;
            const specialita = document.getElementById("png-specialita").value;
            const resultBox = document.getElementById("png-result");
            resultBox.innerHTML = "";
            if (!species || !specialita || !name) {
                resultBox.innerHTML += "<p>Per favore, seleziona nome, specie e specialità.</p>";
                return;
            }

            const speciesChars = speciesData[species].caratteristiche;
            const specialitaChars = specialitaData[specialita].caratteristiche;
            const randomDicePool = dicePools[Math.floor(Math.random() * dicePools.length)].slice();
            const randomLifeDice = lifeDicePools[Math.floor(Math.random() * lifeDicePools.length)];
            
            shuffleArray(randomDicePool);
            const speciesDice = randomDicePool.slice(0, 3);
            shuffleArray(randomDicePool);
            const specialitaDice = randomDicePool.slice(0, 3);
            
            const lifeDice1 = randomLifeDice[0];
            const lifeDice2 = randomLifeDice[1];

            const startingLumen = Math.floor(Math.random() * 4 + 1) * 10;
            
            const equipSlots = { 1: '-', 2: '-', 3: '-', 4: '-', 5: '-', 6: '-', 7: '-', 8: '-', 9: '-', 10: '-' };
            const inventorySlots = {1: '-', 2: '-', 3: '-', 4: '-'};
            const equip = specialitaData[specialita].equipaggiamento;
            const innesti = specialitaData[specialita].innesti;

            if (equip) {
                equip.forEach(item => {
                    if (item.slot.includes('Inventario')) {
                        const slots = item.slot.replace('Inventario ', '').split('-').map(s => parseInt(s.trim()));
                        const randomSlot = slots[Math.floor(Math.random() * slots.length)];
                        inventorySlots[randomSlot] = item.nome;
                    } else if (item.slot.includes('-')) {
                        const slots = item.slot.split('-').map(s => parseInt(s.trim()));
                        const randomSlot = slots[Math.floor(Math.random() * slots.length)];
                        equipSlots[randomSlot] = item.nome;
                    } else {
                        equipSlots[parseInt(item.slot)] = item.nome;
                    }
                });
            }
            if (innesti) {
                innesti.forEach(item => {
                    if (item.slot.includes('-')) {
                        const slots = item.slot.split('-').map(s => parseInt(s.trim()));
                        const randomSlot = slots[Math.floor(Math.random() * slots.length)];
                        equipSlots[randomSlot] = item.nome;
                    } else {
                        equipSlots[parseInt(item.slot)] = item.nome;
                    }
                });
            }

            let output = `
                <div id="png-sheet">
                    <table>
                        <thead>
                            <tr><th colspan="2">Scheda PNG: ${name}</th></tr>
                        </thead>
                        <tbody>
                            <tr><td><strong>Specie:</strong></td><td>${species}</td></tr>
                            <tr><td><strong>Specialità:</strong></td><td>${specialita}</td></tr>
                            <tr><td><strong>Dadi Vita:</strong></td><td>Slot 1: ${lifeDice1}, Slot 2: ${lifeDice2}</td></tr>
                            <tr><td><strong>Lumen Iniziali:</strong></td><td>${startingLumen}</td></tr>
                            <tr>
                                <td><strong>Caratteristiche Specie:</strong></td>
                                <td>${speciesChars[0]}: ${speciesDice[0]}, ${speciesChars[1]}: ${speciesDice[1]}, ${speciesChars[2]}: ${speciesDice[2]}</td>
                            </tr>
                            <tr>
                                <td><strong>Caratteristiche Specialità:</strong></td>
                                <td>${specialitaChars[0]}: ${specialitaDice[0]}, ${specialitaChars[1]}: ${specialitaDice[1]}, ${specialitaChars[2]}: ${specialitaDice[2]}</td>
                            </tr>
                            <tr><td><strong>Peculiarità Specie:</strong></td><td>${speciesData[species].peculiarita}</td></tr>
                            <tr><td><strong>Peculiarità Specialità:</strong></td><td>${specialitaData[specialita].peculiarita}</td></tr>
                        </tbody>
                    </table>
            
                    <h4>Inventario, Equipaggiamento & Innesti Cibernetici</h4>
                    <table>
                        <thead>
                            <tr><th>Slot</th><th>Nome</th></tr>
                        </thead>
                        <tbody>
                            <tr><td>Inventario 1</td><td>${inventorySlots[1]}</td></tr>
                            <tr><td>Inventario 2</td><td>${inventorySlots[2]}</td></tr>
                            <tr><td>Inventario 3</td><td>${inventorySlots[3]}</td></tr>
                            <tr><td>Inventario 4</td><td>${inventorySlots[4]}</td></tr>
                            <tr><td>Fiale di Simbyomax</td><td>2</td></tr>
                        </tbody>
                    </table>
                    <table>
                        <thead>
                            <tr><th>Slot</th><th>Nome</th></tr>
                        </thead>
                        <tbody>
                            <tr><td>1. Testa (E)</td><td>${equipSlots[1] || '-'}</td></tr>
                            <tr><td>2. Corpo (E)</td><td>${equipSlots[2] || '-'}</td></tr>
                            <tr><td>3. Arto Sup DX (E)</td><td>${equipSlots[3] || '-'}</td></tr>
                            <tr><td>4. Arto Sup SX (E)</td><td>${equipSlots[4] || '-'}</td></tr>
                            <tr><td>5. Testa (IC)</td><td>${equipSlots[5] || '-'}</td></tr>
                            <tr><td>6. Corpo (IC)</td><td>${equipSlots[6] || '-'}</td></tr>
                            <tr><td>7. Arto Sup DX (IC)</td><td>${equipSlots[7] || '-'}</td></tr>
                            <tr><td>8. Arto Sup SX (IC)</td><td>${equipSlots[8] || '-'}</td></tr>
                            <tr><td>9. Arto Inf DX (IC)</td><td>${equipSlots[9] || '-'}</td></tr>
                            <tr><td>10. Arto Inf SX (IC)</td><td>${equipSlots[10] || '-'}</td></tr>
                        </tbody>
                    </table>
                </div>
            `;
            resultBox.innerHTML = output;
        }

        function generateAberration() {
            const name = document.getElementById("ab-name").value || "Aberrazione Sconosciuta";
            const species = document.getElementById("ab-species").value;
            const state = document.getElementById("ab-state").value;
            const level = document.getElementById("ab-level").value;
            const resultBox = document.getElementById("ab-result");
            resultBox.innerHTML = "";
        
            if (!species || !state || !level) {
                resultBox.innerHTML += "<p>Per favore, seleziona nome, specie, stato e livello.</p>";
                return;
            }
        
            const diceMap = { "Basso": "D8", "Medio": "D10", "Alto": "D12" };
            const dice = diceMap[level];
        
            const abSpeciesChars = abSpeciesData[species].caratteristiche;
            const abStateChars = abStateData[state].caratteristiche;
            
            const fullDescription = `${abSpeciesData[species].descrizione} ${abStateData[state].descrizione}`;
        
            let output = `
                <div id="ab-sheet">
                    <table>
                        <thead>
                            <tr><th colspan="2">Scheda Aberrazione: ${name}</th></tr>
                        </thead>
                        <tbody>
                            <tr><td><strong>Specie:</strong></td><td>${species}</td></tr>
                            <tr><td><strong>Stato:</strong></td><td>${state}</td></tr>
                            <tr><td><strong>Livello:</strong></td><td>${level}</td></tr>
                            <tr><td><strong>Descrizione:</strong></td><td>${fullDescription}</td></tr>
                            <tr>
                                <td><strong>Caratteristiche:</strong></td>
                                <td>
                                    <ul>
                                        <li>${abSpeciesChars[0]}: ${dice}</li>
                                        <li>${abSpeciesChars[1]}: ${dice}</li>
                                        <li>${abStateChars[0]}: ${dice}</li>
                                        <li>${abStateChars[1]}: ${dice}</li>
                                    </ul>
                                </td>
                            </tr>
                            <tr><td><strong>Dadi Vita:</strong></td><td>4 x ${dice}</td></tr>
                            <tr><td><strong>Peculiarità Specie:</strong></td><td>${abPeculiaritaData[species]}</td></tr>
                            <tr><td><strong>Peculiarità Stato:</strong></td><td>${abPeculiaritaData[state]}</td></tr>
                        </tbody>
                    </table>
                </div>
            `;
            resultBox.innerHTML = output;
        }
        
        document.getElementById("png-species").addEventListener("change", populateNames);
        document.getElementById("generate-png").addEventListener("click", generatePNG);
        document.getElementById("generate-ab").addEventListener("click", generateAberration);
    </script>
</body>
</html>ttps:/
