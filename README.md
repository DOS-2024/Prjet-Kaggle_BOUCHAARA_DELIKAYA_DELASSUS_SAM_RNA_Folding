# Prjet-Kaggle_BOUCHAARA_DELIKAYA_DELASSUS_SAM_RNA_Folding
Stanford Ribonanza RNA Folding
Prédiction du repliement local de l’ARN par apprentissage profond
## 📘 Présentation du projet
Ce projet a été réalisé dans le cadre du Master 2 Bioinformatique – UE Intelligence Artificielle Avancée (2025–2026).
L’objectif est de prédire les profils de réactivité chimique (DMS et 2A3) le long des séquences d’ARN, à partir de leur seule composition nucléotidique, en s’appuyant sur des modèles d’apprentissage profond.
Les données proviennent de la compétition Ribonanza RNA Folding organisée par l’Université de Stanford sur Kaggle.
Elles résultent d’expériences de cartographie chimique couplée au séquençage (MaP-seq), où la réactivité mesurée à chaque position reflète l’accessibilité structurale du nucléotide.
L’objectif est donc de prédire ces signaux expérimentaux directement à partir de la séquence — une étape clé vers la prédiction in silico de la structure secondaire de l’ARN.
## ⚙️ Pipeline et méthodologie
Prétraitement et filtrage : sélection sur rapport signal/bruit (SNR > 1), nombre de lectures (>100), suppression des réplicas.
Encodage One-Hot : représentation des nucléotides (A, C, G, U) sous forme de vecteurs 4D.
Normalisation robuste : z-score basé sur la médiane et la MAD pour atténuer les outliers.
Padding et masquage : gestion des séquences de longueur variable (max = 457 nt).
## 🧠 Modèles testés
LSTM simple – baseline séquentielle
BiLSTM – capture du contexte bidirectionnel
LSTM + Convolutions 1D dilatées – intégration des motifs locaux multi-échelles
Transformer – deux blocs d’attention multi-têtes pour les dépendances longues
Tous les modèles produisent une sortie positionnelle (L×2) et sont entraînés avec une MSE masquée, puis évalués via MAE, MSE et RMSE.
## 📈 Résultats
Modèle	MAE (test)	MSE (test)
LSTM simple	2.47	8.94
BiLSTM	1.07	3.49
LSTM + Conv1D	1.10	3.68
Transformer	1.20	4.34
Le BiLSTM offre le meilleur compromis entre précision, robustesse et coût computationnel.
Le Transformer, bien que plus coûteux, montre un fort potentiel pour de plus grands jeux de données.
## 👩‍💻 Auteurs
Dahirou SAM · Bilal DELIKAYA · Karim BOUCHAARA · Anaïs DELASSUS
Master 2 Bioinformatique – Université Paris Cité (2025–2026)
