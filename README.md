LAB 7 : Analyse Dynamique Mobile avec MobSF
🎯 Objectif

Mettre en place un environnement d’analyse dynamique Android en utilisant un émulateur AVD sans Play Store et préparer MobSF.

🧪 Étape 1 : Création de l’émulateur AVD sans Play Store
La création d’un émulateur Android (AVD) sans Google Play Store est une étape essentielle pour garantir un environnement adapté à l’analyse dynamique avec MobSF. En effet, les images système contenant Google Play intègrent des mécanismes de sécurité supplémentaires (comme Play Protect) qui peuvent bloquer ou fausser l’exécution d’applications vulnérables utilisées en test, telles que DIVA. En choisissant une image basée sur Google APIs sans Play Store, avec une version stable comme Android 10 (API 29) ou Android 11 (API 30), on obtient un environnement plus flexible, compatible avec les outils d’analyse, et plus facile à manipuler (root, instrumentation, etc.). Cette configuration permet ainsi d’effectuer des tests de sécurité dans des conditions contrôlées et reproductibles.

<img width="674" height="497" alt="image" src="https://github.com/user-attachments/assets/69566a49-d7fc-47e4-8ab9-5e2e43d15c54" />

<img width="523" height="233" alt="image" src="https://github.com/user-attachments/assets/bc6af05f-ac86-45c9-a8d4-ede3bbf1244e" />


🧪 Étape 2 : Cloner MobSF
Le clonage du dépôt officiel de MobSF permet de récupérer l’ensemble des outils nécessaires à l’analyse de sécurité mobile, notamment les scripts dédiés à l’analyse dynamique sur émulateur Android. Cette étape est importante car elle garantit l’utilisation d’une version à jour et complète du framework, incluant les modules d’automatisation, l’interface web d’analyse, ainsi que les configurations adaptées aux environnements de test. En travaillant directement à partir du dépôt officiel hébergé sur GitHub, on s’assure également de bénéficier des dernières mises à jour et correctifs de sécurité, ce qui est essentiel dans un contexte d’analyse fiable et reproductible.

Cloner le repository MobSF :

<img width="457" height="22" alt="image" src="https://github.com/user-attachments/assets/e71c2ebc-632a-4af6-8ccd-649ef2a6992b" />
<img width="518" height="114" alt="image" src="https://github.com/user-attachments/assets/2bc3a549-2a80-4981-a257-c5c810ab705c" />

Accéder au dossier :

<img width="260" height="29" alt="image" src="https://github.com/user-attachments/assets/36f295eb-93e4-4879-b899-6cfa552af09b" />

