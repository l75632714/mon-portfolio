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
        .affiche
        
