🧼 User Validator – Module de Validation & Sanitation
Ce module JavaScript permet de valider les données d’un utilisateur et de nettoyer les entrées pour éviter les erreurs ou les injections. Il respecte les principes de lisibilité, fiabilité et maintenabilité du clean code.

📦 Installation
bash
npm init -y
Ajoute ton fichier userValidator.js (ou autre nom) dans ton projet, puis importe-le :

js
const { validateEmail, validateAge, validateUser, sanitize } = require('./userValidator')
🧪 Fonctions disponibles
validateEmail(email: string): boolean
Vérifie si une adresse email est bien formatée.

js
validateEmail('anais@example.com') // true
validateEmail('anais@')            // false
validateAge(age: number): boolean
Vérifie que l’âge est un nombre entre 0 et 150 inclus.

js
validateAge(25)   // true
validateAge(200)  // false
validateUser(user: { name, email, age }): boolean
Valide un objet utilisateur complet. Lève une erreur si une propriété est invalide.

js
const user = {
  name: 'Anaïs',
  email: 'anais@example.com',
  age: 22
}

validateUser(user) // true
sanitize(input: string | number): string
Nettoie une entrée en supprimant les espaces et les caractères < >.

js
sanitize('  <script>hello</script>  ') // "script>hello</script"
📚 Exemple complet
js
try {
  const rawUser = {
    name: sanitize(' Anaïs '),
    email: sanitize('anais@example.com'),
    age: 22
  }

  if (validateUser(rawUser)) {
    console.log('✅ Utilisateur valide !')
  }
} catch (err) {
  console.error('❌ Erreur :', err.message)
}
✅ Bonnes pratiques appliquées
Responsabilité unique : chaque fonction fait une seule chose.

Validation claire : erreurs explicites et ciblées.

Sanitization : protection contre les entrées malveillantes.

Lisibilité : noms explicites, structure logique.
