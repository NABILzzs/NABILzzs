<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulaire Bon de Livraison</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        form {
            max-width: 600px;
            margin: auto;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            font-weight: bold;
            margin-bottom: 5px;
        }
        input, select, textarea {
            width: 100%;
            padding: 8px;
            box-sizing: border-box;
        }
        button {
            padding: 10px 15px;
            background-color: #28a745;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
    </style>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const form = document.getElementById('bon-livraison-form');
            form.addEventListener('submit', async (event) => {
                event.preventDefault(); // Empêche la soumission normale du formulaire

                const formData = new FormData(form);
                const data = Object.fromEntries(formData.entries());

                try {
                    const response = await fetch('https://your-backend-url.com/api/save-bon', { // Remplacez par l'URL de votre backend
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json',
                        },
                        body: JSON.stringify(data),
                    });

                    if (response.ok) {
                        alert('Bon de livraison enregistré avec succès !');
                        form.reset();
                    } else {
                        alert('Erreur lors de l'enregistrement.');
                    }
                } catch (error) {
                    console.error('Erreur :', error);
                    alert('Une erreur est survenue. Veuillez réessayer.');
                }
            });
        });
    </script>
</head>
<body>
    <h1>Bon de Livraison</h1>
    <form id="bon-livraison-form">
        <!-- Informations générales -->
        <div class="form-group">
            <label for="numero-bon">Numéro de Bon</label>
            <input type="text" id="numero-bon" name="numero-bon" required>
        </div>
        <div class="form-group">
            <label for="date">Date</label>
            <input type="date" id="date" name="date" required>
        </div>

        <!-- Informations client -->
        <h2>Informations Client</h2>
        <div class="form-group">
            <label for="nom-client">Nom du Client</label>
            <input type="text" id="nom-client" name="nom-client" required>
        </div>
        <div class="form-group">
            <label for="adresse-client">Adresse</label>
            <textarea id="adresse-client" name="adresse-client" rows="3" required></textarea>
        </div>
        <div class="form-group">
            <label for="telephone-client">Téléphone</label>
            <input type="tel" id="telephone-client" name="telephone-client">
        </div>

        <!-- Détails de la commande -->
        <h2>Détails de la Livraison</h2>
        <div class="form-group">
            <label for="produit">Produit</label>
            <input type="text" id="produit" name="produit" required>
        </div>
        <div class="form-group">
            <label for="quantite">Quantité</label>
            <input type="number" id="quantite" name="quantite" required>
        </div>
        <div class="form-group">
            <label for="prix-unitaire">Prix Unitaire (€)</label>
            <input type="number" id="prix-unitaire" name="prix-unitaire" step="0.01" required>
        </div>
        <div class="form-group">
            <label for="commentaires">Commentaires</label>
            <textarea id="commentaires" name="commentaires" rows="3"></textarea>
        </div>

        <button type="submit">Enregistrer</button>
    </form>
</body>
</html>
