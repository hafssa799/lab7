# LAB 7 : Analyse Dynamique Mobile avec MobSF

 # Objectif

L’objectif de ce laboratoire est de mettre en place un environnement complet d’analyse dynamique des applications Android en utilisant l’outil MobSF, associé à un émulateur Android (AVD) configuré spécifiquement pour les tests de sécurité.

Ce laboratoire vise à permettre à l’étudiant de comprendre et maîtriser les techniques d’analyse en temps réel du comportement d’une application mobile, contrairement à l’analyse statique qui se limite à l’étude du code.
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

![](https://github.com/user-attachments/assets/4fcc9f13-c124-4071-a2dc-ac619103b79d)

## Téléchargement :

# Site officiel : 
       http://www.payatu.com/damn-insecure-and-vulnerable-app/
# Source GitHub : 
       https://github.com/payatu/diva-android
       
![](https://github.com/user-attachments/assets/c1d4ee29-3f12-44b4-bcbb-8f9e9ebb87b0)

# Étape 6 : Analyse avec MobSF

# 6.1 Analyse statique

La première étape consiste à analyser l’APK sans l’exécuter.

1. Dans MobSF (Mobile Security Framework) :

2. importer le fichier APK via Upload & Analyze

3. attendre la génération automatique du rapport

💡 Cette analyse permet d’extraire :

- les permissions Android

- le fichier manifest

- le code décompilé

- les composants exposés

📊 Résultat observé :

![](https://github.com/user-attachments/assets/7c45ee24-681f-4297-8725-02db012af1f6)

 - score de sécurité faible → application vulnérable

 - présence de composants exportés

 - absence de mécanismes de protection avancés

# 6.2 Analyse dynamique

Contrairement à l’analyse statique, ici l’application est exécutée dans un environnement contrôlé.

# Option A — Depuis le tableau de bord "Apps Available

Naviguez vers Dynamic Analyzer → la liste des APKs disponibles s'affiche.

![](https://github.com/user-attachments/assets/958de178-f197-4fa9-b014-ec1848348921)

L'APK DivaApplication.apk (package jakhar.aseem.diva) est listée avec les actions disponibles : "Start Dynamic Analysis", "Start Dynamic Analysis (No reinstall)", et "View Report".

# Option B — Depuis le rapport statique
Cliquez sur le bouton vert "Start Dynamic Analysis" directement dans le rapport statique.

MobSF effectue automatiquement :

✅ Installation de DIVA sur l'émulateur via ADB.

✅ Lancement de Frida Server pour l'instrumentation dynamique.

✅ Configuration du proxy HTTPS global pour intercepter tout le trafic réseau.

✅ Ouverture de l'interface Dynamic Analyzer.


# 6.3 Interface d’analyse

# L’environnement de test est composé de :

- écran de l’émulateur (visualisation de l’app)

- logs système en temps réel

- outils d’analyse réseau

- éditeur de scripts Frida

![](https://github.com/user-attachments/assets/083606d7-1b5c-4d58-83cb-f98b1302b786)

🎯 Cela permet de surveiller le comportement de l’application pendant son exécution.

# 6.4 Analyse des logs (Logcat)

Le flux Logcat permet d’observer les messages générés par l’application.

# Intérêt :

- détecter des informations sensibles exposées

- repérer des erreurs ou comportements anormaux

![](https://github.com/user-attachments/assets/1d6bea7b-a759-47ab-be6c-de4dba67fb8b)

# 6.5 Tests de sécurité réseau

MobSF exécute plusieurs vérifications liées au protocole HTTPS :

- configuration TLS

- résistance au MITM

- vérification du SSL Pinning

- trafic en clair
  
  ![](https://github.com/user-attachments/assets/25152025-f5c6-44a8-838f-3eda97f080b2)

💡 Ces tests permettent de voir si l’application protège correctement ses communications réseau.

# 6.6 Exploration des vulnérabilités

Pendant l’analyse dynamique, on peut tester différents scénarios directement depuis l’émulateur.

🔓 Exemple 1 : Contrôle d’accès

- Certaines activités peuvent être lancées sans authentification → problème de sécurité.

  ![](https://github.com/user-attachments/assets/4010c8ec-d8e7-4879-adf3-76e256eb6d39)

💣 Exemple 2 : Validation des entrées

Des champs mal sécurisés peuvent provoquer :

- crash de l’application

- comportement inattendu

 ![](https://github.com/user-attachments/assets/331f8460-002a-41f9-bea9-56c7020ee35d)

# 6.7 — Instrumentation avec Frida

MobSF intègre une bibliothèque de scripts Frida prêts à l’emploi permettant d’effectuer de l’instrumentation dynamique sur une application Android. Cette fonctionnalité permet d’intercepter, modifier ou observer le comportement de l’application en temps réel.

🔸1. Contournement de la détection d’émulateur

✔ Script utilisé : bypass-emulator-detection

Capture : Frida Code Editor avec le script chargé
![](https://github.com/user-attachments/assets/6dd0d62a-66f4-4126-b0cb-f9f5c9088dbe)

Statut : Script injecté avec succès

MobSF propose le script bypass-emulator-detection, développé par @Areizen_, permettant de contourner les mécanismes de détection d’émulateur implémentés dans certaines applications.

# Fonctionnalités du script

Ce script neutralise plusieurs méthodes de détection, notamment :

- bypass_build_properties() → falsifie les propriétés système (Build.MODEL, BRAND…)

- bypass_phonenumber() → masque les numéros de téléphone

- bypass_deviceid() → falsifie l’IMEI

- bypass_imsi() → masque l’IMSI

- bypass_operator_name() → modifie l’opérateur réseau

🔸 2. Injection du script Frida

La section Instrumentation de MobSF propose plusieurs modes d’exécution :

- Spawn & Inject → lance l’application puis injecte le script

- Inject → injecte dans une application déjà lancée

- Attach → attache Frida à un processus existant

✅ Résultat

Le script est injecté dans le contexte de l’application cible, permettant de modifier son comportement en temps réel.

🔸 3. Interception des clés de chiffrement

✔ Script utilisé : crypto-aes-key

Capture : Frida + crypto-aes-key + accès root
![](https://github.com/user-attachments/assets/2d4ec3cf-45ce-471b-9bd7-92671203b3dd)

Statut : Script actif avec interception réussie

Ce script permet d’intercepter les clés AES utilisées par l’application.

# Fonctionnement

Il hook la classe Java suivante : javax.crypto.spec.SecretKeySpec

📊 Résultat

- Les clés AES sont capturées en clair

- Affichage en format hexadécimal

- Observation directe des données sensibles utilisées par l’application

🔸 4. Accès root et Shell

MobSF fournit un accès direct au terminal via :

[root@android] #

✔ Utilisation

- Navigation dans le système Android

- Lecture/écriture de fichiers sensibles

- Interaction directe avec l’application

🔸 5. Code Frida injecté

Capture : fenêtre "Injected Frida Script"
![](https://github.com/user-attachments/assets/49786f8f-7023-43cc-a36d-3d2844ea7676)

MobSF affiche le code JavaScript complet injecté dans l’application.

🔍 Contenu du script

- Bridge Frida ↔ Java (Frida 17+)

- Fonctions utilitaires :

✔ getLoadedClasses() → liste des classes chargées

✔ getAllMethods() → liste des méthodes disponibles

# 6.8 Rapport final

À la fin de l’analyse, MobSF génère un rapport complet contenant :

- logs système

- trafic réseau capturé

- résultats des tests de sécurité

![](https://github.com/user-attachments/assets/71bd28b3-3e5e-426c-b442-070291aac706)

# Étape 7 : Tests avancés

Après l’analyse de base, il est possible d’aller plus loin.

🔍 Exploration manuelle

Pour chaque challenge DIVA :

1. Lancez l'activité correspondante depuis l'émulateur.

2. Observez les logs dans le Logcat Stream de MobSF.

3. Analysez le trafic réseau capturé dans HTTP(S) Traffic.

4. Vérifiez les fichiers créés via File Monitor.

On peut injecter du code pour surveiller des méthodes spécifiques.

Java.perform(function() {
    var MainActivity = Java.use("jakhar.aseem.diva.MainActivity");

    MainActivity.someMethod.implementation = function() {
        console.log("[*] someMethod() intercepted!");

        // Appel de la méthode originale
        var result = this.someMethod.apply(this, arguments);

        return result;
    };
});

# Conclusion 

Le LAB 7 a permis de configurer un émulateur Android sans Play Store et d’installer MobSF pour réaliser des analyses statiques et dynamiques d’APK vulnérables. L’application DIVA a servi de cas pratique, révélant des failles comme le stockage non sécurisé et les credentials codés en dur. L’analyse dynamique sur émulateur rooté a montré le comportement réel de l’application, tandis que MobSF a fourni un rapport clair des vulnérabilités. Ce laboratoire illustre l’importance d’un environnement contrôlé pour tester la sécurité des applications mobiles de manière fiable et reproductible.
