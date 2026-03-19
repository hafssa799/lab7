# LAB 7 : Analyse Dynamique Mobile avec MobSF

 # Objectif

Mettre en place un environnement d’analyse dynamique Android en utilisant un émulateur AVD sans Play Store et préparer MobSF.

# Étape 1 : Création de l’émulateur AVD sans Play Store
La création d’un émulateur Android (AVD) sans Google Play Store est une étape essentielle pour garantir un environnement adapté à l’analyse dynamique avec MobSF. En effet, les images système contenant Google Play intègrent des mécanismes de sécurité supplémentaires (comme Play Protect) qui peuvent bloquer ou fausser l’exécution d’applications vulnérables utilisées en test, telles que DIVA. En choisissant une image basée sur Google APIs sans Play Store, avec une version stable comme Android 10 (API 29) ou Android 11 (API 30), on obtient un environnement plus flexible, compatible avec les outils d’analyse, et plus facile à manipuler (root, instrumentation, etc.). Cette configuration permet ainsi d’effectuer des tests de sécurité dans des conditions contrôlées et reproductibles.

![](https://github.com/user-attachments/assets/69566a49-d7fc-47e4-8ab9-5e2e43d15c54)

![](https://github.com/user-attachments/assets/bc6af05f-ac86-45c9-a8d4-ede3bbf1244e)


# Étape 2 : Cloner MobSF
Le clonage du dépôt officiel de MobSF permet de récupérer l’ensemble des outils nécessaires à l’analyse de sécurité mobile, notamment les scripts dédiés à l’analyse dynamique sur émulateur Android. Cette étape est importante car elle garantit l’utilisation d’une version à jour et complète du framework, incluant les modules d’automatisation, l’interface web d’analyse, ainsi que les configurations adaptées aux environnements de test. En travaillant directement à partir du dépôt officiel hébergé sur GitHub, on s’assure également de bénéficier des dernières mises à jour et correctifs de sécurité, ce qui est essentiel dans un contexte d’analyse fiable et reproductible.

Cloner le repository MobSF :

![](https://github.com/user-attachments/assets/e71c2ebc-632a-4af6-8ccd-649ef2a6992b)
![](https://github.com/user-attachments/assets/2bc3a549-2a80-4981-a257-c5c810ab705c)

# Relancer MobSF :

![](https://github.com/user-attachments/assets/36f295eb-93e4-4879-b899-6cfa552af09b)

Ensuite tapez :
![](https://github.com/user-attachments/assets/77a860ed-13ec-410f-a0b6-cfe7148d15d7)
Attendez que l’installation se termine
![](https://github.com/user-attachments/assets/e32b2c70-69cf-4164-82a4-aa1a9a5ff70e)

# Étape 3 : Lancement de l’émulateur pour MobSF

Démarrer un émulateur Android rooté et prêt pour l’analyse dynamique avec MobSF.

1️⃣ Se placer dans le dossier MobSF

![](https://github.com/user-attachments/assets/4d0e5fbf-ccb3-47e9-b73c-52b5ab456e7c)

2️⃣ Lister les AVD disponibles
Affiche tous les AVD disponibles

![](https://github.com/user-attachments/assets/d51a817a-e25a-4269-8425-85c2614e0c89)

Indique la syntaxe pour lancer un AVD spécifique
3️⃣Lancer l’émulateur

![](https://github.com/user-attachments/assets/5703a211-b617-426e-8204-4bf76f5b28c8)

# Le script :

- Démarre l’émulateur sur le port 5554

- Attend que l’émulateur boot complètement

- Redémarre adb en root

- Tente de désactiver AVB et verity (les erreurs sont normales sur Windows)

Remonte le système de fichiers pour l’analyse dynamique

4️⃣ Vérifier que l’émulateur est détecté

![](https://github.com/user-attachments/assets/358c6a14-c321-4c82-a699-699e9909bd5b)

# Étape 4 : Installation et lancement de MobSF via Docker

Lancer MobSF en utilisant Docker pour effectuer des analyses dynamiques sur l’émulateur Android.

1️⃣ Télécharger l’image MobSF

![](https://github.com/user-attachments/assets/e8eb887a-348a-4b46-a117-c6cce5cd102d)

2️⃣ Lancer MobSF en indiquant l’ID de l’émulateur

![](https://github.com/user-attachments/assets/940c3891-383f-4caa-8803-9ac5c3787539)

![](https://github.com/user-attachments/assets/b55697c9-590b-440a-a668-9be6362b5862)

- L’option -p 8000:8000 expose MobSF sur le port 8000.
  
- L’option -it --rm permet de lancer MobSF en mode interactif et de supprimer le conteneur à la fermeture.

3️⃣ Accéder à MobSF

Ouvre ton navigateur et va sur :  http://127.0.0.1:8000

![](https://github.com/user-attachments/assets/8f9ff954-679f-4579-a8d5-19cd81bbe33c)

![](https://github.com/user-attachments/assets/f234e73b-169e-46fb-a61e-2fe514f39edb)

# Étape 5 : Téléchargement de l’APK DIVA

Dans cette étape, nous avons téléchargé l’application vulnérable DIVA (Damn Insecure and Vulnerable App), utilisée pour tester les outils d’analyse de sécurité mobile.

DIVA contient 13 challenges de sécurité, couvrant plusieurs types de vulnérabilités :

<img width="263" height="329" alt="image" src="https://github.com/user-attachments/assets/4fcc9f13-c124-4071-a2dc-ac619103b79d" />

# Site officiel : 
       http://www.payatu.com/damn-insecure-and-vulnerable-app/
# Source GitHub : 
       https://github.com/payatu/diva-android
![](https://github.com/user-attachments/assets/c1d4ee29-3f12-44b4-bcbb-8f9e9ebb87b0)

Étape 5 : Récupération de l’application DIVA

Pour réaliser les tests de sécurité, on utilise une application volontairement vulnérable appelée DIVA (Damn Insecure and Vulnerable App).

Cette application a été conçue spécialement pour l’apprentissage de la sécurité mobile. Elle regroupe plusieurs scénarios réels de vulnérabilités que l’on peut rencontrer dans des applications Android.

👉 Elle contient 13 cas pratiques, parmi lesquels :
#	Challenge	Type de vulnérabilité
1	Insecure Logging	Fuite d'infos dans les logs
2	Hardcoded Issues Part 1	Credentials en dur dans le code
3	Insecure Data Storage Part 1	SharedPreferences non sécurisées
4	Insecure Data Storage Part 2	Base de données SQLite non chiffrée
5	Insecure Data Storage Part 3	Fichiers temp non sécurisés
6	Insecure Data Storage Part 4	Stockage externe non sécurisé
7	Input Validation Issues Part 1	Injection SQL
8	Input Validation Issues Part 2	XSS via WebView
9	Access Control Issues Part 1	Activités exportées accessibles
10	Access Control Issues Part 2	Content Provider exposé
11	Access Control Issues Part 3	Activités protégées contournables
12	Hardcoded Issues Part 2	JNI / code natif hardcodé
13	Input Validation Issues Part 3	Buffer overflow / validation native

stockage de données non sécurisé

identifiants codés en dur

problèmes de validation des entrées

failles de contrôle d’accès

vulnérabilités liées au code natif

📥 Téléchargement :

Site officiel : Payatu

GitHub : dépôt open source

Une fois téléchargé, le fichier APK est placé localement pour être utilisé dans l’outil d’analyse.

🔎 Étape 6 : Analyse avec MobSF
6.1 Analyse statique

La première étape consiste à analyser l’APK sans l’exécuter.

Dans MobSF (Mobile Security Framework) :

importer le fichier APK via Upload & Analyze

attendre la génération automatique du rapport

💡 Cette analyse permet d’extraire :

les permissions Android

le fichier manifest

le code décompilé

les composants exposés

📊 Résultat observé :

score de sécurité faible → application vulnérable

présence de composants exportés

absence de mécanismes de protection avancés

6.2 Analyse dynamique

Contrairement à l’analyse statique, ici l’application est exécutée dans un environnement contrôlé.

Deux façons de lancer l’analyse :

depuis la liste des applications disponibles

directement depuis le rapport statique

⚙️ Automatiquement, MobSF :

installe l’application via ADB

configure un proxy pour intercepter le trafic réseau

active Frida pour l’instrumentation

lance l’émulateur Android

6.3 Interface d’analyse

L’environnement de test est composé de :

écran de l’émulateur (visualisation de l’app)

logs système en temps réel

outils d’analyse réseau

éditeur de scripts Frida

🎯 Cela permet de surveiller le comportement de l’application pendant son exécution.

6.4 Analyse des logs (Logcat)

Le flux Logcat permet d’observer les messages générés par l’application.

👉 Intérêt :

détecter des informations sensibles exposées

repérer des erreurs ou comportements anormaux

Exemple :

affichage de mots de passe ou tokens → faille de logging

6.5 Tests de sécurité réseau

MobSF exécute plusieurs vérifications liées au protocole HTTPS :

configuration TLS

résistance au MITM

vérification du SSL Pinning

trafic en clair

💡 Ces tests permettent de voir si l’application protège correctement ses communications réseau.

6.6 Exploration des vulnérabilités

Pendant l’analyse dynamique, on peut tester différents scénarios directement depuis l’émulateur.

🔓 Exemple 1 : Contrôle d’accès

Certaines activités peuvent être lancées sans authentification → problème de sécurité.

💣 Exemple 2 : Validation des entrées

Des champs mal sécurisés peuvent provoquer :

crash de l’application

comportement inattendu

6.7 Instrumentation avec Frida

L’outil Frida permet d’interagir avec l’application en temps réel.

Exemples d’utilisation :

contourner la détection d’émulateur

intercepter des méthodes Java

récupérer des données sensibles en mémoire

👉 Cela permet de simuler des attaques avancées sans modifier l’APK.

6.8 Rapport final

À la fin de l’analyse, MobSF génère un rapport complet contenant :

logs système

trafic réseau capturé

résultats des tests de sécurité

captures d’écran

📄 Ce rapport peut être exporté pour documentation ou présentation.

🧪 Étape 7 : Tests avancés

Après l’analyse de base, il est possible d’aller plus loin.

🔍 Exploration manuelle

tester chaque fonctionnalité de l’application

observer les réactions dans les logs

analyser les fichiers générés

🧠 Scripts personnalisés

On peut injecter du code pour surveiller des méthodes spécifiques.

🚧 Contournement des protections

bypass SSL Pinning

bypass Root Detection

accès aux composants internes

📤 Export des résultats

Les résultats peuvent être sauvegardés sous forme de rapport détaillé pour analyse ou présentation.
# Conclusion 

Le LAB 7 a permis de configurer un émulateur Android sans Play Store et d’installer MobSF pour réaliser des analyses statiques et dynamiques d’APK vulnérables. L’application DIVA a servi de cas pratique, révélant des failles comme le stockage non sécurisé et les credentials codés en dur. L’analyse dynamique sur émulateur rooté a montré le comportement réel de l’application, tandis que MobSF a fourni un rapport clair des vulnérabilités. Ce laboratoire illustre l’importance d’un environnement contrôlé pour tester la sécurité des applications mobiles de manière fiable et reproductible.
