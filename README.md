# Mon portfolio

Mon portfolio


<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mon Portfolio Mixed Media - Galerie d'Affiches</title>
    <style>
        :root {
            --bg-color: #F7F5F0;
            --text-color: #2C3E50;
            --accent-sage: #8A9A86;
            --accent-sand: #D4B996;
            --accent-rose: #D6A28E;
            --accent-blue: #9FB1C1;
            --card-bg: #FFFFFF;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            padding: 40px 20px;
            position: relative;
            min-height: 100vh;
        }

        /* En-tête */
        header {
            max-width: 1200px;
            margin: 0 auto 40px auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid var(--text-color);
            padding-bottom: 20px;
        }

        .header-titles h1 {
            font-size: 2.2rem;
            letter-spacing: -0.5px;
        }

        .header-titles p {
            font-size: 1rem;
            opacity: 0.8;
            margin-top: 4px;
        }

        .btn-toggle-edit {
            background-color: var(--accent-sage);
            color: white;
            border: 2px solid var(--text-color);
            padding: 10px 20px;
            font-weight: bold;
            border-radius: 4px;
            cursor: pointer;
            box-shadow: 3px 3px 0px var(--text-color);
            transition: all 0.2s ease;
        }

        .btn-toggle-edit:hover {
            transform: translate(-2px, -2px);
            box-shadow: 5px 5px 0px var(--text-color);
        }

        /* Grille Masonry d'Affiches */
        .grid-affiches {
            column-count: 3;
            column-gap: 24px;
            max-width: 1200px;
            margin: 0 auto;
        }

        @media (max-width: 900px) { .grid-affiches { column-count: 2; } }
        @media (max-width: 600px) { .grid-affiches { column-count: 1; } }

        /* Composant Affiche */
        .affiche {
            break-inside: avoid;
            margin-bottom: 24px;
            background-color: var(--card-bg);
            border: 2px solid var(--text-color);
            box-shadow: 4px 4px 0px var(--text-color);
            position: relative;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
            overflow: hidden;
        }

        .affiche:hover {
            transform: translate(-2px, -2px);
            box-shadow: 6px 6px 0px var(--text-color);
        }

        /* Formes de cadre */
        .shape-droite { border-radius: 4px; }
        .shape-asymetrique { border-radius: 24px 4px 18px 4px; }
        .shape-organique { border-radius: 40px 15px 35px 20px / 20px 35px 15px 40px; }
        .shape-polaroid { border-radius: 2px; padding: 12px 12px 0 12px; background: #fff; }

        /* Textures */
        .texture-lisse { background-image: none; }
        .texture-papier {
            background-image: radial-gradient(#000000 0.5px, transparent 0.5px);
            background-size: 8px 8px;
            background-color: rgba(255, 255, 255, 0.95);
            background-blend-mode: overlay;
        }
        .texture-kraft {
            background-color: #E8D3B9;
            background-image: repeating-linear-gradient(45deg, rgba(0,0,0,0.02) 0px, rgba(0,0,0,0.02) 2px, transparent 2px, transparent 4px);
        }
        .texture-grain {
            background-image: repeating-radial-gradient(circle at 17% 32%, rgba(0,0,0,0.05), rgba(0,0,0,0.05) 1px, transparent 1px, transparent 100px);
        }

        /* Zone visuel de l'affiche */
        .affiche-visuel {
            width: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 1.2rem;
            text-align: center;
            padding: 20px;
            background-position: center;
            background-size: cover;
        }

        .h-petite { height: 180px; }
        .h-moyenne { height: 260px; }
        .h-grande { height: 350px; }

        /* Contenu de l'affiche */
        .affiche-corps {
            padding: 16px;
            border-top: 2px solid var(--text-color);
        }

        .affiche-titre {
            font-size: 1.1rem;
            margin-bottom: 10px;
            font-weight: 700;
        }

        .affiche-badge {
            display: inline-block;
            padding: 4px 10px;
            border-radius: 3px;
            font-size: 0.75rem;
            font-weight: bold;
            text-transform: uppercase;
            border: 1.5px solid var(--text-color);
            box-shadow: 2px 2px 0px var(--text-color);
        }

        /* Commandes d'édition sur l'affiche */
        .affiche-actions {
            position: absolute;
            top: 10px;
            right: 10px;
            display: none;
            gap: 6px;
            z-index: 10;
        }

        .mode-edition-actif .affiche-actions {
            display: flex;
        }

        .btn-action {
            background: white;
            border: 1.5px solid var(--text-color);
            padding: 4px 8px;
            font-size: 0.75rem;
            font-weight: bold;
            cursor: pointer;
            border-radius: 3px;
            box-shadow: 2px 2px 0px var(--text-color);
        }

        .btn-action:hover {
            background: var(--bg-color);
        }

        /* Bouton Ajouter Affiche Flottant */
        .btn-ajouter-affiche {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background-color: var(--accent-rose);
            color: white;
            font-size: 2rem;
            border: 2px solid var(--text-color);
            box-shadow: 4px 4px 0px var(--text-color);
            cursor: pointer;
            display: none;
            align-items: center;
            justify-content: center;
            transition: all 0.2s ease;
            z-index: 99;
        }

        .mode-edition-actif .btn-ajouter-affiche {
            display: flex;
        }

        .btn-ajouter-affiche:hover {
            transform: scale(1.05);
            box-shadow: 6px 6px 0px var(--text-color);
        }

        /* Modal de création / modification d'affiche */
        .modal-overlay {
            position: fixed;
            top: 0; left: 0; right: 0; bottom: 0;
            background: rgba(0,0,0,0.5);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 1000;
        }

        .modal-fenetre {
            background: var(--bg-color);
            border: 2px solid var(--text-color);
            box-shadow: 8px 8px 0px var(--text-color);
            width: 90%;
            max-width: 500px;
            padding: 24px;
            border-radius: 8px;
        }

        .modal-titre {
            font-size: 1.4rem;
            margin-bottom: 16px;
            border-bottom: 2px solid var(--text-color);
            padding-bottom: 8px;
        }

        .form-champ {
            margin-bottom: 14px;
        }

        .form-champ label {
            display: block;
            font-size: 0.85rem;
            font-weight: bold;
            margin-bottom: 4px;
            text-transform: uppercase;
        }

        .form-champ input, .form-champ select {
            width: 100%;
            padding: 8px;
            border: 2px solid var(--text-color);
            border-radius: 4px;
            font-family: inherit;
        }

        .modal-boutons {
            display: flex;
            justify-content: flex-end;
            gap: 12px;
            margin-top: 20px;
        }

        .btn-secondaire {
            background: white;
            border: 2px solid var(--text-color);
            padding: 8px 16px;
            font-weight: bold;
            cursor: pointer;
            border-radius: 4px;
        }

        .btn-primaire {
            background: var(--accent-sage);
            color: white;
            border: 2px solid var(--text-color);
            padding: 8px 16px;
            font-weight: bold;
            cursor: pointer;
            border-radius: 4px;
            box-shadow: 2px 2px 0px var(--text-color);
        }
    </style>
</head>
<body>

    <header>
        <div class="header-titles">
            <h1>Atelier Mixed Media</h1>
            <p>Galerie d'affiches, créations IA & collages</p>
        </div>
        <button class="btn-toggle-edit" id="toggleEditBtn" onclick="toggleModeEdition()">Mode Édition : OFF</button>
    </header>

    <main class="grid-affiches" id="galerieAffiches">
        <!-- Les affiches seront générées dynamiquement via JS -->
    </main>

    <!-- Bouton d'ajout flottant -->
    <button class="btn-ajouter-affiche" onclick="ouvrirModalAjout()" title="Créer une nouvelle affiche">+</button>

    <!-- Modal Formulaire -->
    <div class="modal-overlay" id="modalForm">
        <div class="modal-fenetre">
            <h2 class="modal-titre" id="modalTitreText">Nouvelle Affiche</h2>
            <form id="afficheForm" onsubmit="sauvegarderAffiche(event)">
                <input type="hidden" id="afficheId">
                
                <div class="form-champ">
                    <label for="titreInput">Titre de l'affiche</label>
                    <input type="text" id="titreInput" required placeholder="Ex: Composition géométrique n°4">
                </div>

                <div class="form-champ">
                    <label for="badgeInput">Type de contenu (Badge)</label>
                    <input type="text" id="badgeInput" required placeholder="Ex: Mixed Media, Visuel IA, Article...">
                </div>

                <div class="form-champ">
                    <label for="tailleSelect">Format de l'affiche</label>
                    <select id="tailleSelect">
                        <option value="h-petite">Petite hauteur</option>
                        <option value="h-moyenne" selected>Hauteur moyenne</option>
                        <option value="h-grande">Grande hauteur</option>
                    </select>
                </div>

                <div class="form-champ">
                    <label for="couleurSelect">Couleur d'accentuation</label>
                    <select id="couleurSelect">
                        <option value="var(--accent-sage)">Vert Sauge</option>
                        <option value="var(--accent-sand)">Sable Chaud</option>
                        <option value="var(--accent-rose)">Rose Poudré</option>
                        <option value="var(--accent-blue)">Bleu Poudré</option>
                    </select>
                </div>

                <div class="form-champ">
                    <label for="formeSelect">Forme du cadre</label>
                    <select id="formeSelect">
                        <option value="shape-droite">Lignes droites nettes</option>
                        <option value="shape-asymetrique">Coins asymétriques</option>
                        <option value="shape-organique">Forme organique (Blob)</option>
                        <option value="shape-polaroid">Format Polaroid</option>
                    </select>
                </div>

                <div class="form-champ">
                    <label for="textureSelect">Texture de surface</label>
                    <select id="textureSelect">
                        <option value="texture-papier">Effet Papier Grainé</option>
                        <option value="texture-kraft">Effet Papier Kraft</option>
                        <option value="texture-grain">Effet Grain Photo</option>
                        <option value="texture-lisse">Lisse / Sans texture</option>
                    </select>
                </div>

                <div class="modal-boutons">
                    <button type="button" class="btn-secondaire" onclick="fermerModal()">Annuler</button>
                    <button type="submit" class="btn-primaire">Enregistrer l'affiche</button>
                </div>
            </form>
        </div>
    </div>

    <script>
        // Données initiales des affiches
        const affichesInitiales = [
            {
                id: 1,
                titre: "Exploration des formes géométriques",
                badge: "Mixed Media",
                taille: "h-moyenne",
                couleur: "var(--accent-sage)",
                forme: "shape-asymetrique",
                texture: "texture-papier"
            },
            {
                id: 2,
                titre: "Réflexion sur l'art génératif",
                badge: "Article",
                taille: "h-grande",
                couleur: "var(--accent-rose)",
                forme: "shape-droite",
                texture: "texture-kraft"
            },
            {
                id: 3,
                titre: "Superposition d'encres et aplats",
                badge: "Visuel IA",
                taille: "h-petite",
                couleur: "var(--accent-blue)",
                forme: "shape-organique",
                texture: "texture-grain"
            }
        ];

        let affiches = JSON.parse(localStorage.getItem('affichesPortfolio')) || affichesInitiales;
        let modeEdition = false;

        function enregistrerLocalement() {
            localStorage.setItem('affichesPortfolio', JSON.stringify(affiches));
        }

        function toggleModeEdition() {
            modeEdition = !modeEdition;
            const btn = document.getElementById('toggleEditBtn');
            const body = document.body;

            if (modeEdition) {
                btn.textContent = "Mode Édition : ON";
                btn.style.backgroundColor = "var(--accent-rose)";
                body.classList.add('mode-edition-actif');
            } else {
                btn.textContent = "Mode Édition : OFF";
                btn.style.backgroundColor = "var(--accent-sage)";
                body.classList.remove('mode-edition-actif');
            }
        }

        function afficherAffiches() {
            const conteneur = document.getElementById('galerieAffiches');
            conteneur.innerHTML = '';

            affiches.forEach(a => {
                const el = document.createElement('article');
                el.className = `affiche ${a.forme} ${a.texture}`;
                
                el.innerHTML = `
                    <div class="affiche-actions">
                        <button class="btn-action" onclick="editerAffiche(${a.id})">Éditer</button>
                        <button class="btn-action" style="color: #c0392b;" onclick="supprimerAffiche(${a.id})">✕</button>
                    </div>
                    <div class="affiche-visuel ${a.taille}" style="background-color: ${a.couleur}">
                        <span>${a.titre}</span>
                    </div>
                    <div class="affiche-corps">
                        <h3 class="affiche-titre">${a.titre}</h3>
                        <span class="affiche-badge" style="background-color: ${a.couleur}">${a.badge}</span>
                    </div>
                `;
                conteneur.appendChild(el);
            });
        }

        function ouvrirModalAjout() {
            document.getElementById('afficheForm').reset();
            document.getElementById('afficheId').value = '';
            document.getElementById('modalTitreText').textContent = 'Nouvelle Affiche';
            document.getElementById('modalForm').style.display = 'flex';
        }

        function editerAffiche(id) {
            const a = affiches.find(item => item.id === id);
            if (!a) return;

            document.getElementById('afficheId').value = a.id;
            document.getElementById('titreInput').value = a.titre;
            document.getElementById('badgeInput').value = a.badge;
            document.getElementById('tailleSelect').value = a.taille;
            document.getElementById('couleurSelect').value = a.couleur;
            document.getElementById('formeSelect').value = a.forme;
            document.getElementById('textureSelect').value = a.texture;

            document.getElementById('modalTitreText').textContent = 'Modifier l\'Affiche';
            document.getElementById('modalForm').style.display = 'flex';
        }

        function fermerModal() {
            document.getElementById('modalForm').style.display = 'none';
        }

        function sauvegarderAffiche(e) {
            e.preventDefault();
            const id = document.getElementById('afficheId').value;
            
            const nouvelleAffiche = {
                id: id ? parseInt(id) : Date.now(),
                titre: document.getElementById('titreInput').value,
                badge: document.getElementById('badgeInput').value,
                taille: document.getElementById('tailleSelect').value,
                couleur: document.getElementById('couleurSelect').value,
                forme: document.getElementById('formeSelect').value,
                texture: document.getElementById('textureSelect').value
            };

            if (id) {
                const index = affiches.findIndex(item => item.id === parseInt(id));
                affiches[index] = nouvelleAffiche;
            } else {
                affiches.push(nouvelleAffiche);
            }

            enregistrerLocalement();
            afficherAffiches();
            fermerModal();
        }

        function supprimerAffiche(id) {
            if (confirm("Voulez-vous vraiment supprimer cette affiche ?")) {
                affiches = affiches.filter(item => item.id !== id);
                enregistrerLocalement();
                afficherAffiches();
            }
        }

        // Initialisation au chargement
        afficherAffiches();
    </script>
</body>
</html>
