# Sécurité des données : analyse et exigences

Ce document fait le point sur la sécurité de Bomba Archives : l'état de la démonstration actuelle, les menaces pour la version réelle, les protections à exiger du développeur et le cadre juridique en RDC.

*Dernière mise à jour : 16 novembre 2026.*

## En bref

**La démonstration n'est pas sécurisée, et ce n'est pas son rôle.** Elle sert à montrer le produit avec des données fictives. Elle ne doit **jamais recevoir de vrais documents**. Dans la version réelle, la sécurité doit être assurée par le serveur.

## 1. Les données concernées

| Données | Clients | Sensibilité |
|---|---|---|
| Dossiers médicaux, résultats d'analyses | Cliniques | Très élevée : traitement interdit en principe par le Code du numérique, sauf exceptions |
| Dossiers d'élèves, souvent mineurs | Écoles | Élevée |
| Dossiers de procédure, actes | Avocats, notaires | Élevée : secret professionnel |
| Dossiers du personnel, salaires | Tous | Élevée |
| Factures, comptabilité | Tous | Moyenne |

## 2. État de la démonstration

| Point | Situation dans la démo | Risque avec de vraies données |
|---|---|---|
| Connexion | Aucune : le menu « Connecté en tant que » permet d'être n'importe qui | N'importe qui voit tout |
| Droits d'accès | Vérifiés seulement dans le navigateur | Contournables |
| Stockage | En clair, dans le stockage local du navigateur | Lisible par toute personne qui utilise l'ordinateur |
| Cloisonnement des clients | Un seul stockage partagé | Un client pourrait voir les données d'un autre |
| Journal d'audit | Modifiable | Sans valeur de preuve |
| Signature électronique | Image ou nom tapé | Sans valeur juridique |
| Dépendances | Google Fonts et cdnjs (QR codes) | En production, héberger ces fichiers soi-même |

Règle du dépôt : **n'y mettre ni vraies données, ni mot de passe, ni clé d'accès.**

## 3. Menaces pour la version réelle

1. Vol de mots de passe (hameçonnage par e-mail ou WhatsApp, mots de passe faibles).
2. Abus interne : un employé du client ou de Bomba qui consulte ou copie des dossiers.
3. Fuite pendant la numérisation : photos au téléphone, clé USB, carton égaré.
4. Perte de données : panne de disque, coupures d'électricité, incendie, inondation.
5. Rançongiciel qui chiffre les fichiers.
6. Vol de matériel : ordinateur portable, disque de sauvegarde.
7. Hébergement à l'étranger sans garanties suffisantes.

## 4. Protections à exiger

**Identité et accès**
- Mots de passe solides et double authentification obligatoire.
- Droits vérifiés par le serveur à chaque requête.
- Déconnexion automatique après inactivité, blocage après plusieurs essais ratés.
- Retrait immédiat des accès d'une personne qui part.

**Chiffrement**
- HTTPS partout.
- Fichiers, base de données et sauvegardes chiffrés.

**Cloisonnement des clients**
- Un client ne doit techniquement pas pouvoir atteindre les données d'un autre, et ce point doit être testé.

**Traçabilité**
- Journal d'audit non modifiable, même par un administrateur, conservé à part.

**Sauvegardes**
- Règle 3-2-1 : trois copies, deux supports différents, une copie hors des locaux.
- Au moins une copie impossible à modifier, contre les rançongiciels.
- Test de restauration chaque mois.

**Application**
- Mises à jour de sécurité régulières.
- Contrôle des fichiers déposés.
- Test d'intrusion par un spécialiste avant le lancement.

**Sécurité physique**
- Magasin d'archives fermé, avec registre des entrées.
- Pas de téléphone personnel pendant la numérisation.
- Bordereau signé à chaque remise de cartons.
- Numérisation sur place pour les dossiers médicaux.

**Organisation**
- Engagement de confidentialité signé par chaque employé.
- Formation contre l'hameçonnage.
- Procédure écrite en cas d'incident.
- Une personne responsable de la protection des données.

**Signature et copies certifiées**
- Signature électronique avec certificat et horodatage, par un prestataire reconnu.
- QR codes menant vers une page de vérification publique et sécurisée.

## 5. Cadre juridique en RDC

Texte principal : **ordonnance-loi n° 23/010 du 13 mars 2023 portant Code du numérique**.

- **Consentement** préalable et explicite, prouvable et révocable.
- **Données de santé** : traitement interdit en principe, sauf exceptions (consentement explicite pour un but précis, traitement lié à la santé).
- **Formalités** : déclaration pour tout traitement ; autorisation pour les données les plus sensibles et pour les transferts vers l'étranger.
- **Hébergement à l'étranger** : permis seulement si le pays offre une protection au moins équivalente.
- **Violations de données** : à signaler sans délai à l'autorité de protection.
- **Amendes** : de 3 000 à 70 000 $.

L'Autorité de protection des données (APD) n'est pas encore en fonctionnement. Un arrêté ministériel du 17 août 2024 a confié provisoirement ses missions à l'ARPTIC, une solution contestée par des juristes. Un réseau national de responsables de la protection des données a été lancé à Kinshasa le 12 mars 2026.

**Rôle de Bomba :** le client reste responsable de ses données ; Bomba agit pour son compte comme sous-traitant. Chaque contrat doit prévoir la confidentialité, la sécurité, le lieu d'hébergement, la notification des incidents, et la restitution ou destruction des données en fin de contrat.

Ces points doivent être validés par un avocat qui connaît le Code du numérique avant la signature du premier contrat.

## 6. Les 10 priorités avant le premier vrai client

1. Aucune vraie donnée dans la démo.
2. Connexion sécurisée avec double authentification obligatoire.
3. Droits vérifiés par le serveur et cloisonnement entre clients testé.
4. Chiffrement des données et des sauvegardes.
5. Sauvegardes 3-2-1, dont une impossible à modifier, et test de restauration mensuel.
6. Journal d'audit impossible à modifier.
7. Hébergement conforme au Code du numérique, inscrit dans les contrats.
8. Contrat de sous-traitance et engagements de confidentialité.
9. Procédure d'incident écrite.
10. Test d'intrusion avant le lancement.

## Sources

- [DLA Piper – Data Protection in the Democratic Republic of Congo](https://www.dlapiperdataprotection.com/?c=CD&t=law)
- [We Are Tech Africa – La RDC met en place un réseau de responsables de la protection des données](https://www.wearetech.africa/fr/fils/actualites/tech/numerique-la-rdc-met-en-place-un-reseau-de-responsables-de-la-protection-des-donnees)
- [Code du numérique – RD Congo (Droit-Numérique.cd)](https://droitnumerique.cd/wp-content/uploads/2024/08/Code-du-numerique-I-RD-Congo.pdf)
