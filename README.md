# Bomba Archives

**« Kobomba » : garder, en lingala.**

Bomba Archives est une plateforme de numérisation et de gestion électronique de documents (GED) pensée pour les organisations de Kinshasa : écoles, cliniques, cabinets d'avocats, ONG et entreprises.

Ce dépôt contient la **démonstration interactive** de la plateforme. C'est une page web unique (`index.html`), sans serveur. Elle sert à présenter le produit aux futurs clients et à cadrer le travail du développeur qui construira la version réelle.

## Ouvrir la démonstration

- **Sur votre ordinateur :** téléchargez `index.html` et ouvrez-le dans un navigateur récent (Chrome, Edge, Firefox).
- **En ligne avec GitHub Pages :** dans le dépôt, allez dans *Settings > Pages*, choisissez la branche `main` et le dossier `/ (root)`, puis enregistrez. La démo sera publiée à l'adresse indiquée par GitHub.

Les données sont des exemples. Vos modifications restent dans votre navigateur. Le bouton « Réinitialiser la démo », en bas du menu, rétablit les données de départ.

Pour une présentation, cliquez sur **« Lancer la visite guidée »** : 11 étapes font le tour de la plateforme. Sur téléphone, le bouton se trouve dans le « Menu ».

Le bouton « Sauvegarder ou restaurer la démo » permet de copier les données de la démo pour les retrouver sur un autre appareil.

**Sécurité :** la démo ne doit jamais recevoir de vrais documents. Voir [SECURITE.md](SECURITE.md) pour l'analyse complète et les exigences de la version réelle.

## Les modules

### Espace client

| Module | Rôle |
|---|---|
| Tableau de bord | Tâches, lots en cours, échéances, documents récents |
| Mes tâches | Parapheur électronique (validation et signature), délais, délégation pendant une absence, mentions |
| Archives | Recherche dans le texte et dans les fiches, syntaxe avancée (`type:`, `tag:`, `"expression"`, `-exclure`), vues enregistrées, vue tableau et actions groupées |
| Visionneuse | Aperçu avec filigrane, fiche d'indexation, étiquettes, documents liés, versions avec extraction, annotations, copies certifiées, historique |
| Boîte de dépôt | Capture depuis le scanner, l'e-mail ou WhatsApp, avec règles de classement automatique |
| Nouveau document | Cote automatique, fiche d'indexation selon le type, durée de conservation |
| Courrier | Registre du courrier arrivé et départ, délais de réponse, archivage en un clic |
| Demandes | Accès temporaire aux documents confidentiels, livraison des originaux papier |
| Conservation | Échéances, gel juridique, bordereau et registre des éliminations |
| Copies certifiées | Copies avec code unique et QR code, vérification d'authenticité, révocation |
| Rapports | Consultations, documents les plus consultés, activité par utilisateur, export CSV |
| Corbeille | Restauration ; suppression définitive bloquée tant que la conservation court |
| Utilisateurs | Rôles, accès par service, double authentification |
| Circuits de validation | Étapes de validation et de signature par type de document, avec délais et relances |
| Sécurité | Score de sécurité, règles d'accès, sauvegardes 3-2-1, liens de partage |
| Intégrations | Scanner, e-mail, WhatsApp, Microsoft 365, Google Drive, API |
| Journal d'audit | Trace de chaque action |

### Espace Bomba (prestataire)

| Module | Rôle |
|---|---|
| Pilotage | Chiffre d'affaires, revenus réguliers, impayés, qualité, occupation du magasin |
| Prospects | Suivi commercial du premier contact à la signature |
| Lots et production | Les 7 étapes de numérisation, avec contrôle qualité |
| Missions | Collectes, livraisons, sessions sur site, par équipe et véhicule |
| Magasin d'archives | Emplacement et suivi de chaque carton |
| Clients | Fiche et chiffres de chaque client |
| Facturation | Factures mensuelles, paiements M-Pesa, Orange Money, Airtel Money ou virement |
| Dépenses et marge | Dépenses par poste et résultat mensuel |
| Devis | Chiffrage d'un projet |
| Paramètres | Tarifs, formules d'abonnement, référentiel de conservation |

## Comptes de démonstration

Changez de compte avec le menu « Connecté en tant que ».

| Client | Administrateur | Gestionnaire | Lecteur |
|---|---|---|---|
| Complexe Scolaire Les Étoiles (Lemba) | Nadine Kabeya | Patrick Mbuyi | Grâce Nsimba |
| Polyclinique Tujenge (Ngaliema) | Dr Serge Ilunga | Ruth Mwamba | Éric Tshibangu |
| Cabinet Me Lukusa & Associés (Gombe) | Me Jean-Pierre Lukusa | Me Esther Kalala | Didier Bokele |

Les organisations, les personnes et les documents sont fictifs.

## Ce qui reste à construire pour la version réelle

La démonstration simule plusieurs fonctions qui demandent un serveur :

1. **Stockage et comptes** : base de données, stockage chiffré des fichiers, connexion sécurisée, double authentification par SMS.
2. **Lecture automatique du texte (OCR)** des PDF et des images, en français.
3. **Signature électronique à valeur juridique** : certificat et horodatage.
4. **Envois réels** : relances et notifications par SMS et par e-mail, dépôt par e-mail et WhatsApp.
5. **Sauvegardes** selon la règle 3-2-1 et tests de restauration.
6. **Conformité** : vérifier les règles de la RDC sur la protection des données et la valeur juridique des copies numériques, avec un juriste.

Pour démarrer vite, la version serveur peut s'appuyer sur un logiciel libre de gestion documentaire, comme Paperless-ngx ou Mayan EDMS, avant un développement sur mesure.

## Technique

- Une seule page HTML, avec CSS et JavaScript intégrés, sans dépendance à installer.
- Polices chargées depuis Google Fonts. Bibliothèque `qrcode-generator` chargée depuis cdnjs pour les QR codes ; sans elle, la page affiche le code à la place.
- Interface en français, adaptée au téléphone (menu repliable), thèmes clair et sombre.
- Qualité : annulation des actions sensibles, messages d'erreur sous les champs, navigation au clavier (`/`, `Ctrl K`, `?`), fenêtres accessibles, affichage par paquets de 25 documents, mise en page pour l'impression.
- Données de démonstration enregistrées dans le stockage local du navigateur.
