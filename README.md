# mon-portfolio
mon-portfolio
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio Mixed Media</title>
    <style>
        :root {
            --bg-color: #F7F5F0;
            --text-color: #2C3E50;
            --accent-sage: #8A9A86;
            --accent-sand: #D4B996;
            --accent-rose: #D6A28E;
            --accent-blue: #9FB1C1;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            font-family: system-ui, -apple-system, sans-serif;
            margin: 0;
            padding: 40px 20px;
        }

        /* Disposition Masonry type Pinterest */
        .masonry-grid {
            column-count: 3;
            column-gap: 24px;
            max-width: 1200px;
            margin: 0 auto;
        }

        @media (max-width: 900px) { .masonry-grid { column-count: 2; } }
        @media (max-width: 600px) { .masonry-grid { column-count: 1; } }

        /* Carte avec formes et lignes mixtes */
        .card {
            break-inside: avoid;
            margin-bottom: 24px;
            background: #ffffff;
            border: 2px solid var(--text-color);
            border-radius: 16px 4px 20px 4px; /* Découpe légèrement asymétrique */
            overflow: hidden;
            box-shadow: 4px 4px 0px var(--text-color);
            transition: transform 0.2s ease;
        }

        .card:hover {
            transform: translate(-2px, -2px);
            box-shadow: 6px 6px 0px var(--text-color);
        }

        /* Simulates des hauteurs et des formes organiques différentes */
        .card-media {
            width: 100%;
            display: block;
            object-fit: cover;
        }

        .h-short { height: 180px; }
        .h-medium { height: 260px; }
        .h-tall { height: 340px; }

        .card-content {
            padding: 16px;
            border-top: 2px solid var(--text-color);
        }

        .card-title {
            margin: 0 0 8px 0;
            font-size: 1.1rem;
        }

        .card-tag {
            display: inline-block;
            padding: 4px 10px;
            border-radius: 12px;
            font-size: 0.75rem;
            font-weight: bold;
            text-transform: uppercase;
        }
    </style>
</head>
<body>

    <main class="masonry-grid">
        <article class="card">
            <div class="card-media h-medium" style="background-color: var(--accent-sage);"></div>
            <div class="card-content">
                <h3 class="card-title">Collage géométrique n°1</h3>
                <span class="card-tag" style="background: var(--accent-sand);">Mixed Media</span>
            </div>
        </article>

        <article class="card">
            <div class="card-media h-tall" style="background-color: var(--accent-rose);"></div>
            <div class="card-content">
                <h3 class="card-title">Article : Explorer l'IA créative</h3>
                <span class="card-tag" style="background: var(--accent-blue);">Écrit</span>
            </div>
        </article>

        <article class="card">
            <div class="card-media h-short" style="background-color: var(--accent-blue);"></div>
            <div class="card-content">
                <h3 class="card-title">Formes organiques & Encre</h3>
                <span class="card-tag" style="background: var(--accent-sage);">Illustration</span>
            </div>
        </article>
    </main>

</body>
</html>
