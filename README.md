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

- Stockage non sécurisé (Insecure Storage)

- Credentials codés en dur (Hardcoded Credentials)

- Intents non sécurisés

- Logging sensible

- Code natif vulnérable

![](https://github.com/user-attachments/assets/c1d4ee29-3f12-44b4-bcbb-8f9e9ebb87b0)

# Étape 6 : Analyse statique et dynamique avec MobSF

 1. Analyse statique

L’application diva.apk a été importée dans MobSF via : Upload & Analyze

![](https://github.com/user-attachments/assets/190c1ddb-7836-4ac0-80e8-8962492358a6)

2. Analyse dynamique

Après l’analyse statique, nous avons lancé : Start Dynamic Analyzer

![](https://github.com/user-attachments/assets/d8b98282-4206-47cd-82dc-ec6c4f849bd3)

# Conclusion 

Le LAB 7 a permis de configurer un émulateur Android sans Play Store et d’installer MobSF pour réaliser des analyses statiques et dynamiques d’APK vulnérables. L’application DIVA a servi de cas pratique, révélant des failles comme le stockage non sécurisé et les credentials codés en dur. L’analyse dynamique sur émulateur rooté a montré le comportement réel de l’application, tandis que MobSF a fourni un rapport clair des vulnérabilités. Ce laboratoire illustre l’importance d’un environnement contrôlé pour tester la sécurité des applications mobiles de manière fiable et reproductible.
