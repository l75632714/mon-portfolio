# Portfolio

Portfolio

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

        /* Pied de page (Footer Copyright) */
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
            <button class="btn-header" style="background-color: var(--accent-sand);" id="btnAdminPanneau" onclick="ouvrirStats()">📊 Stats & Modération</button>
            <button class="btn-header" id="toggleEditBtn" onclick="toggleModeEdition()">Mode Édition : OFF</button>
        </div>
    </header>

    <main class="grid-affiches" id="galerieAffiches"></main>

    <!-- Pied de page avec Copyright -->
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
                <div class="form-champ">
                    <label for="urlInput">Lien Web / Réseau Social (URL)</label>
                    <input type="url" id="urlInput" placeholder="https://instagram.com/..., https://pinterest.com/...">
                </div>
                <div class="form-champ">
                    <label for="badgeInput">Type de contenu (Badge)</label>
                    <input type="text" id="badgeInput" required placeholder="Ex: Instagram, Pinterest, Article...">
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
        let m

                                                                                

            
