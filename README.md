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
            padding: 40px 20px 20px 20px;
            position: relative;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        /* En-tête */
        header {
            max-width: 1200px;
            width: 100%;
            margin: 0 auto 40px auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid var(--text-color);
            padding-bottom: 20px;
            flex-wrap: wrap;
            gap: 15px;
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

        .header-actions {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .btn-header {
            background-color: var(--accent-sage);
            color: white;
            border: 2px solid var(--text-color);
            padding: 10px 16px;
            font-weight: bold;
            border-radius: 4px;
            cursor: pointer;
            box-shadow: 3px 3px 0px var(--text-color);
            transition: all 0.2s ease;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 6px;
            font-size: 0.9rem;
        }

        .btn-header:hover {
            transform: translate(-2px, -2px);
            box-shadow: 5px 5px 0px var(--text-color);
        }

        /* Grille Masonry d'Affiches */
        .grid-affiches {
            column-count: 3;
            column-gap: 24px;
            max-width: 1200px;
            width: 100%;
            margin: 0 auto;
            flex: 1;
        }

        @media (max-width: 900px) { .grid-affiches { column-count: 2; } }
        @media (max-width: 600px) { .grid-affiches { column-count: 1; } }

        /* Composant Affiche */
        .affiche-wrapper {
            break-inside: avoid;
            margin-bottom: 24px;
            display: block;
        }

        .affiche {
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
            position: relative;
            cursor: pointer;
        }

        .affiche-visuel span {
            background: rgba(0, 0, 0, 0.4);
            padding: 6px 12px;
            border-radius: 4px;
            backdrop-filter: blur(2px);
        }

        .h-petite { height: 180px; }
        .h-moyenne { height: 260px; }
        .h-grande { height: 350px; }

        /* Icone lien externe */
        .affiche-link-icon {
            position: absolute;
            top: 8px;
            left: 8px;
            background: rgba(255, 255, 255, 0.9);
            border: 1.5px solid var(--text-color);
            border-radius: 50%;
            width: 26px;
            height: 26px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.75rem;
            color: var(--text-color);
        }

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

        .affiche-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 10px;
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

        /* Barre d'interaction */
        .affiche-interactions {
            display: flex;
            gap: 8px;
            align-items: center;
        }

        .btn-interact {
            background: white;
            border: 1.5px solid var(--text-color);
            padding: 4px 8px;
            font-size: 0.85rem;
            font-weight: bold;
            cursor: pointer;
            border-radius: 4px;
            display: flex;
            align-items: center;
            gap: 5px;
            box-shadow: 2px 2px 0px var(--text-color);
            transition: all 0.15s ease;
        }

        .btn-interact svg {
            width: 15px;
            height: 15px;
            fill: none;
            stroke: var(--text-color);
            stroke-width: 2;
            stroke-linecap: round;
            stroke-linejoin: round;
        }

        .btn-interact:hover {
            transform: translateY(-1px);
            background: var(--bg-color);
        }

        /* Commandes d'édition */
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

        /* Module de recherche Giphy */
        .giphy-search-box {
            display: flex;
            gap: 8px;
            margin-bottom: 8px;
        }

        .giphy-results-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 8px;
            max-height: 150px;
            overflow-y: auto;
            margin-top: 8px;
            border: 1px solid var(--text-color);
            padding: 6px;
            border-radius: 4px;
            background: white;
        }

        .giphy-results-grid img {
            width: 100%;
            height: 70px;
            object-fit: cover;
            cursor: pointer;
            border: 2px solid transparent;
            border-radius: 3px;
        }

        .giphy-results-grid img:hover {
            border-color: var(--accent-sage);
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

        /* Pied de page */
        footer {
            max-width: 1200px;
            width: 100%;
            margin: 60px auto 0 auto;
            padding-top: 20px;
            border-top: 2px solid var(--text-color);
            text-align: center;
            font-size: 0.9rem;
            font-weight: 600;
            color: var(--text-color);
            opacity: 0.85;
        }

        /* Modals */
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
            max-width: 550px;
            padding: 24px;
            border-radius: 8px;
            max-height: 90vh;
            overflow-y: auto;
        }

        .modal-titre {
            font-size: 1.4rem;
            margin-bottom: 16px;
            border-bottom: 2px solid var(--text-color);
            padding-bottom: 8px;
        }

        .form-champ { margin-bottom: 14px; }
        .form-champ label {
            display: block;
            font-size: 0.85rem;
            font-weight: bold;
            margin-bottom: 4px;
            text-transform: uppercase;
        }
        .form-champ input, .form-champ select, .form-champ textarea {
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

        .stats-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
            margin-bottom: 20px;
        }
        .stat-card {
            background: white;
            border: 2px solid var(--text-color);
            padding: 12px;
            border-radius: 4px;
            text-align: center;
        }
        .stat-value {
            font-size: 1.6rem;
            font-weight: bold;
            color: var(--accent-sage);
        }

        .liste-commentaires {
            margin-top: 15px;
            max-height: 250px;
            overflow-y: auto;
        }
        .comm-item {
            background: white;
            border: 1.5px solid var(--text-color);
            padding: 8px 12px;
            margin-bottom: 8px;
            border-radius: 4px;
            font-size: 0.9rem;
        }
        .comm-auteur { font-weight: bold; font-size: 0.8rem; margin-bottom: 2px; }
        .comm-actions { display: flex; gap: 6px; margin-top: 4px; }
    </style>
</head>
<body>

    <header>
        <div class="header-titles">
            <h1>Atelier Mixed Media</h1>
            <p>Galerie d'affiches, créations IA & collages</p>
        </div>
        <div class="header-actions">
            <!-- Bouton Buy me a drink -->
            <a href="https://buymeacoffee.com/votre_lien" target="_blank" class="btn-header" style="background-color: var(--accent-rose);" title="Offrir un verre">
                ☕ Buy me a drink
            </a>
            <button class="btn-header" style="background-color: var(--accent-sand);" id="btnAdminPanneau" onclick="ouvrirStats()">📊 Stats & Modération</button>
            <button class="btn-header" id="toggleEditBtn" onclick="toggleModeEdition()">Mode Édition : OFF</button>
        </div>
    </header>

    <main class="grid-affiches" id="galerieAffiches"></main>

    <!-- Pied de page -->
    <footer>
        © Tous droits réservés à Louise Émilie Schreiber
    </footer>

    <!-- Bouton Ajouter Affiche Flottant -->
    <button class="btn-ajouter-affiche" onclick="ouvrirModalAjout()" title="Créer une nouvelle affiche">+</button>

    <!-- Modal Formulaire Affiche -->
    <div class="modal-overlay" id="modalForm">
        <div class="modal-fenetre">
            <h2 class="modal-titre" id="modalTitreText">Nouvelle Affiche</h2>
            <form id="afficheForm" onsubmit="sauvegarderAffiche(event)">
                <input type="hidden" id="afficheId">
                
                <div class="form-champ">
                    <label for="titreInput">Titre de l'affiche</label>
                    <input type="text" id="titreInput" required placeholder="Ex: Composition géométrique n°4">
                </div>

                <!-- Option Image / GIF -->
                <div class="form-champ">
                    <label for="bgImageInput">URL de l'image ou du GIF</label>
                    <input type="url" id="bgImageInput" placeholder="https://... (.jpg, .png, .gif)">
                </div>

                <!-- Module de recherche Giphy intégré -->
                <div class="form-champ">
                    <label>Rechercher un GIF sur Giphy</label>
                    <div class="giphy-search-box">
                        <input type="text" id="giphyQuery" placeholder="Ex: art, collage, vintage...">
                        <button type="button" class="btn-secondaire" onclick="rechercherGiphy()">Chercher</button>
                    </div>
                    <div id="giphyResults" class="giphy-results-grid" style="display: none;"></div>
                </div>

                <div class="form-champ">
                    <label for="urlInput">Lien Web externe / Réseau Social (Cliquable)</label>
                    <input type="url" id="urlInput" placeholder="https://instagram.com/..., https://pinterest.com/...">
                </div>

                <div class="form-champ">
                    <label for="badgeInput">Type de contenu (Badge)</label>
                    <input type="text" id="badgeInput" required placeholder="Ex: Instagram, GIF, Article...">
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
                    <label for="couleurSelect">Couleur de fond (si pas d'image/GIF)</label>
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
                    <button type="button" class="btn-secondaire" onclick="fermerModal('modalForm')">Annuler</button>
                    <button type="submit" class="btn-primaire">Enregistrer</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Modal Commentaires -->
    <div class="modal-overlay" id="modalCommentaires">
        <div class="modal-fenetre">
            <h2 class="modal-titre">Commentaires</h2>
            <div id="listeCommModal" class="liste-commentaires"></div>
            <form onsubmit="ajouterCommentaire(event)" style="margin-top: 15px;">
                <input type="hidden" id="commAfficheId">
                <div class="form-champ">
                    <label>Votre Nom</label>
                    <input type="text" id="commNom" required placeholder="Votre prénom ou pseudo">
                </div>
                <div class="form-champ">
                    <label>Votre Commentaire (Liens interdits)</label>
                    <textarea id="commTexte" rows="3" required placeholder="Laissez un mot doux..."></textarea>
                </div>
                <div class="modal-boutons">
                    <button type="button" class="btn-secondaire" onclick="fermerModal('modalCommentaires')">Fermer</button>
                    <button type="submit" class="btn-primaire">Envoyer</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Modal Stats & Modération -->
    <div class="modal-overlay" id="modalStats">
        <div class="modal-fenetre">
            <h2 class="modal-titre">Statistiques & Modération</h2>
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-value" id="statVues">0</div>
                    <small>Visites Totales</small>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="statAffiches">0</div>
                    <small>Affiches</small>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="statLikes">0</div>
                    <small>Empreintes (J'aime)</small>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="statClics">0</div>
                    <small>Clics sur liens</small>
                </div>
            </div>

            <h3 style="font-size: 1.1rem; margin-bottom: 10px;">Modération des commentaires</h3>
            <div id="moderationListe" class="liste-commentaires"></div>

            <div class="modal-boutons">
                <button type="button" class="btn-secondaire" onclick="fermerModal('modalStats')">Fermer</button>
            </div>
        </div>
    </div>

    <script>
        const affichesInitiales = [
            {
                id: 1,
                titre: "Exploration des formes géométriques",
                bgImage: "",
                url: "https://instagram.com",
                badge: "Instagram",
                taille: "h-moyenne",
                couleur: "var(--accent-sage)",
                forme: "shape-asymetrique",
                texture: "texture-papier",
                likes: 5,
                clics: 2
            },
            {
                id: 2,
                titre: "Réflexion sur l'art génératif",
                bgImage: "",
                url: "https://pinterest.com",
                badge: "Pinterest",
                taille: "h-grande",
                couleur: "var(--accent-rose)",
                forme: "shape-droite",
                texture: "texture-kraft",
                likes: 8,
                clics: 4
            }
        ];

        let affiches = JSON.parse(localStorage.getItem('affichesPortfolio')) || affichesInitiales;
        let commentaires = JSON.parse(localStorage.getItem('commentairesPortfolio')) || [];
        let statsVues = parseInt(localStorage.getItem('statsVues') || '1') + 1;
        let modeEdition = false;

        localStorage.setItem('statsVues', statsVues);

        function sauvegarderDonnees() {
            localStorage.setItem('affichesPortfolio', JSON.stringify(affiches));
            localStorage.setItem('commentairesPortfolio', JSON.stringify(commentaires));
        }

        function toggleModeEdition() {
            modeEdition = !modeEdition;
            const btn = document.getElementById('toggleEditBtn');
            if (modeEdition) {
                btn.textContent = "Mode Édition : ON";
                btn.style.backgroundColor = "var(--accent-rose)";
                document.body.classList.add('mode-edition-actif');
            } else {
                btn.textContent = "Mode Édition : OFF";
                btn.style.backgroundColor = "var(--accent-sage)";
                document.body.classList.remove('mode-edition-actif');
            }
        }

        function afficherAffiches() {
            const conteneur = document.getElementById('galerieAffiches');
            conteneur.innerHTML = '';

            affiches.forEach(a => {
                const wrapper = document.createElement('div');
                wrapper.className = 'affiche-wrapper';

                const el = document.createElement('article');
                el.className = `affiche ${a.forme} ${a.texture}`;
                
                const iconLien = a.url ? '<span class="affiche-link-icon" title="Ouvrir le lien">↗</span>' : '';
                const nbComms = commentaires.filter(c => c.afficheId === a.id && c.statut === 'approuve').length;

                const bgStyle = a.bgImage 
                    ? `background-image: url('${a.bgImage}'); background-size: cover; background-position: center;` 
                    : `background-color: ${a.couleur};`;

                const svgEmpreinte = `
                    <svg viewBox="0 0 24 24">
                        <path d="M12 2a10 10 0 0 0-10 10c0 3 1.2 5.8 3.2 7.8" />
                        <path d="M12 6a6 6 0 0 0-6 6c0 1.8.7 3.5 1.9 4.8" />
                        <path d="M12 10a2 2 0 0 0-2 2c0 .6.2 1.2.6 1.6" />
                        <path d="M12 14a2 2 0 0 1 2-2" />
                        <path d="M15 12a3 3 0 0 0-3-3" />
                        <path d="M18 12a6 6 0 0 0-6-6" />
                        <path d="M21 12a9 9 0 0 0-9-9" />
                        <path d="M12 18a6 6 0 0 0 5.2-3" />
                        <path d="M12 22a10 10 0 0 0 8.8-5.2" />
                    </svg>`;

                el.innerHTML = `
                    <div class="affiche-actions">
                        <button class="btn-action" onclick="editerAffiche(event, ${a.id})">Éditer</button>
                        <button class="btn-action" style="color: #c0392b;" onclick="supprimerAffiche(event, ${a.id})">✕</button>
                    </div>
                    <div class="affiche-visuel ${a.taille}" style="${bgStyle}" onclick="ouvrirLien(${a.id}, '${a.url}')">
                        <span>${a.titre}</span>
                        ${iconLien}
                    </div>
                    <div class="affiche-corps">
                        <h3 class="affiche-titre">${a.titre}</h3>
                        <div class="affiche-footer">
                            <span class="affiche-badge" style="background-color: ${a.couleur}">${a.badge}</span>
                            <div class="affiche-interactions">
                                <button class="btn-interact btn-like" onclick="likerAffiche(${a.id})" title="J'aime (Empreinte)">
                                    ${svgEmpreinte} <span>${a.likes || 0}</span>
                                </button>
                                <button class="btn-interact" onclick="partagerAffiche('${a.titre}', '${a.url}')" title="Partager">
                                    ◎
                                </button>
                                <button class="btn-interact" onclick="ouvrirCommentaires(${a.id})" title="Commentaires">
                                    💬 <span>${nbComms}</span>
                                </button>
                            </div>
                        </div>
                    </div>
                `;
                
                wrapper.appendChild(el);
                conteneur.appendChild(wrapper);
            });
        }

        async function rechercherGiphy() {
            const query = document.getElementById('giphyQuery').value;
            const grid = document.getElementById('giphyResults');
            if (!query) return;

            grid.style.display = 'grid';
            grid.innerHTML = 'Chargement...';

            try {
                const apiKey = 'dc6zaTOxFJmzC';
                const res = await fetch(`https://api.giphy.com/v1/gifs/search?q=${encodeURIComponent(query)}&limit=6&api_key=${apiKey}`);
                const data = await res.json();

                grid.innerHTML = '';
                if (data.data && data.data.length > 0) {
                    data.data.forEach(gif => {
                        const img = document.createElement('img');
                        img.src = gif.images.fixed_height_small.url;
                        img.alt = gif.title;
                        img.onclick = () => {
                            document.getElementById('bgImageInput').value = gif.images.original.url;
                            grid.style.display = 'none';
                        };
                        grid.appendChild(img);
                    });
                } else {
                    grid.innerHTML = 'Aucun GIF trouvé.';
                }
            } catch (err) {
                grid.innerHTML = 'Erreur lors de la recherche Giphy.';
            }
        }

        function likerAffiche(id) {
            const a = affiches.find(item => item.id === id);
            if (a) {
                a.likes = (a.likes || 0) + 1;
                sauvegarderDonnees();
                afficherAffiches();
            }
        }

        function partagerAffiche(titre, url) {
            const lienPartage = url || window.location.href;
            if (navigator.share) {
                navigator.share({ title: titre, url: lienPartage });
            } else {
                navigator.clipboard.writeText(lienPartage);
                alert("Lien de l'affiche copié dans le presse-papier !");
            }
        }

        function ouvrirLien(id, url) {
            if (!url || modeEdition) return;
            const a = affiches.find(item => item.id === id);
            if (a) {
                a.clics = (a.clics || 0) + 1;
                sauvegarderDonnees();
            }
            window.open(url, '_blank');
        }

        function verifierLiensIntegrees(texte) {
            const regexLien = /(https?:\/\/|www\.|[a-zA-Z0-9-]+\.[a-zA-Z]{2,})/i;
            return regexLien.test(texte);
        }

        function ajouterCommentaire(e) {
            e.preventDefault();
            const id = parseInt(document.getElementById('commAfficheId').value);
            const nom = document.getElementById('commNom').value;
            const texte = document.getElementById('commTexte').value;

            if (verifierLiensIntegrees(texte) || verifierLiensIntegrees(nom)) {
                alert("Désolé, les liens web ne sont pas autorisés dans les commentaires.");
                return;
            }

            commentaires.push({
                id: Date.now(),
                afficheId: id,
                auteur: nom,
                texte: texte,
                statut: 'en_attente'
            });

            sauvegarderDonnees();
            alert("Commentaire envoyé ! Il apparaîtra après modération.");
            document.getElementById('commTexte').value = '';
            fermerModal('modalCommentaires');
        }

        function ouvrirCommentaires(id) {
            document.getElementById('commAfficheId').value = id;
            const commsAffiche = commentaires.filter(c => c.afficheId === id && c.statut === 'approuve');
            const listeEl = document.getElementById('listeCommModal');
            
            listeEl.innerHTML = commsAffiche.length ? '' : '<p style="opacity: 0.7;">Aucun commentaire pour l\'instant.</p>';
            commsAffiche.forEach(c => {
                listeEl.innerHTML += `
                    <div class="comm-item">
                        <div class="comm-auteur">${c.auteur}</div>
                        <div>${c.texte}</div>
                    </div>
                `;
            });
            document.getElementById('modalCommentaires').style.display = 'flex';
        }

        function ouvrirStats() {
            document.getElementById('statVues').textContent = localStorage.getItem('statsVues') || 1;
            document.getElementById('statAffiches').textContent = affiches.length;
            document.getElementById('statLikes').textContent = affiches.reduce((acc, a) => acc + (a.likes || 0), 0);
            document.getElementById('statClics').textContent = affiches.reduce((acc, a) => acc + (a.clics || 0), 0);

            const modEl = document.getElementById('moderationListe');
            modEl.innerHTML = commentaires.length ? '' : '<p style="opacity: 0.7;">Aucun commentaire à modérer.</p>';
            
            commentaires.forEach(c => {
                modEl.innerHTML += `
                    <div class="comm-item">
                        <div class="comm-auteur">${c.auteur} - <small>Statut: ${c.statut}</small></div>
                        <div>${c.texte}</div>
                        <div class="comm-actions">
                            ${c.statut !== 'approuve' ? `<button class="btn-action" onclick="changerStatutComm(${c.id}, 'approuve')">Approuver</button>` : ''}
                            <button class="btn-action" style="color:red;" onclick="supprimerComm(${c.id})">Supprimer</button>
                        </div>
                    </div>
                `;
            });

            document.getElementById('modalStats').style.display = 'flex';
        }

        function changerStatutComm(id, statut) {
            const c = commentaires.find(item => item.id === id);
            if (c) {
                c.statut = statut;
                sauvegarderDonnees();
                ouvrirStats();
                afficherAffiches();
            }
        }

        function supprimerComm(id) {
            commentaires = commentaires.filter(item => item.id !== id);
            sauvegarderDonnees();
            ouvrirStats();
            afficherAffiches();
        }

        function ouvrirModalAjout() {
            document.getElementById('afficheForm').reset();
            document.getElementById('afficheId').value = '';
            document.getElementById('giphyResults').style.display = 'none';
            document.getElementById('modalTitreText').textContent = 'Nouvelle Affiche';
            document.getElementById('modalForm').style.display = 'flex';
        }

        function editerAffiche(e, id) {
            e.stopPropagation();
            const a = affiches.find(item => item.id === id);
            if (!a) return;

            document.getElementById('afficheId').value = a.id;
            document.getElementById('titreInput').value = a.titre;
            document.getElementById('bgImageInput').value = a.bgImage || '';
            document.getElementById('urlInput').value = a.url || '';
            document.getElementById('badgeInput').value = a.badge;
            document.getElementById('tailleSelect').value = a.taille;
            document.getElementById('couleurSelect').value = a.couleur;
            document.getElementById('formeSelect').value = a.forme;
            document.getElementById('textureSelect').value = a.texture;
            document.getElementById('giphyResults').style.display = 'none';

            document.getElementById('modalTitreText').textContent = 'Modifier l\'Affiche';
            document.getElementById('modalForm').style.display = 'flex';
        }

        function fermerModal(id) { document.getElementById(id).style.display = 'none'; }

        function sauvegarderAffiche(e) {
            e.preventDefault();
            const id = document.getElementById('afficheId').value;
            const nouvelleAffiche = {
                id: id ? parseInt(id) : Date.now(),
                titre: document.getElementById('titreInput').value,
                bgImage: document.getElementById('bgImageInput').value,
                url: document.getElementById('urlInput').value,
                badge: document.getElementById('badgeInput').value,
                taille: document.getElementById('tailleSelect').value,
                couleur: document.getElementById('couleurSelect').value,
                forme: document.getElementById('formeSelect').value,
                texture: document.getElementById('textureSelect').value,
                likes: id ? (affiches.find(a => a.id === parseInt(id))?.likes || 0) : 0,
                clics: id ? (affiches.find(a => a.id === parseInt(id))?.clics || 0) : 0
            };

            if (id) {
                const index = affiches.findIndex(item => item.id === parseInt(id));
                affiches[index] = nouvelleAffiche;
            } else {
                affiches.push(nouvelleAffiche);
            }

            sauvegarderDonnees();
            afficherAffiches();
            fermerModal('modalForm');
        }

        function supprimerAffiche(e, id) {
            e.stopPropagation();
            if (confirm("Supprimer cette affiche ?")) {
                affiches = affiches.filter(item => item.id !== id);
                commentaires = commentaires.filter(c => c.afficheId !== id);
                sauvegarderDonnees();
                afficherAffiches();
            }
        }

        afficherAffiches();
    </script>
</body>
</html>

