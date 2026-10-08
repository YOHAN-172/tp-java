# Réponses TPB1 : environnement Java

**Q1.** Java 25.0.4.1 (Temurin). `java -version` donne la version de la JVM qui exécute le bytecode, `javac -version` celle du compilateur. Un JRE seul n'a pas `javac`.

**Q2.** Un fichier `Bonjour.class` apparaît. Il n'est pas lisible : c'est du bytecode binaire (format .class), exécuté par la JVM.

**Q3.** Java ajoute la compilation (`javac`). Elle détecte avant l'exécution les erreurs de syntaxe et de type.

**Q4.** (à vérifier chez vous) Avec `public class Salut` dans `Bonjour.java` : erreur « class Salut is public, should be declared in a file named Salut.java ». Règle : une classe publique doit porter le nom de son fichier.

**Q5.** (à vérifier) Oui, VS Code souligne en rouge le `;` manquant avant toute exécution. En Python, la parenthèse manquante est aussi signalée par Pylance, mais l'interpréteur ne verrait l'erreur qu'au lancement.

**Q6.** Java refuse de compiler `int x = "texte";` (incompatible types). Python accepte `x: int = "texte"` à l'exécution car les annotations ne sont pas vérifiées par l'interpréteur.

**Q7.** Java : `target/` (+ `*.class`) joue le rôle de `__pycache__/`. On ne versionne pas les fichiers générés : ils se régénèrent, alourdissent le dépôt et créent des conflits inutiles.

**Q8.** Le bloc `<dependency>` (groupId `com.google.code.gson`, artifactId `gson`, version). La version demandée est dans `<version>2.11.0</version>`.

**Q9.** Dans le cache partagé `~/.m2`. Avantage : une seule copie de Gson pour dix projets (gain de place et de téléchargements).

**Q10.** `groupId` (organisation), `artifactId` (nom du projet), `version` identifient un artefact de façon unique pour le publier ou le référencer. Un projet Python simple n'est pas publié ni référencé ainsi, il n'en a donc pas besoin.

**Q11.** `public` : visible partout (pas d'équivalent en Python). `static` : appartient à la classe, appelable sans objet (pas d'équivalent direct). `double` : type de retour décimal (Python utilise `float` en annotation facultative).

**Q12.** (à vérifier) `IllegalArgumentException: La liste est vide`. En Python, `moyenne([])` lève `ZeroDivisionError` si on ne teste pas la liste vide : le comportement dépend du code écrit.

**Q13.** Maven et le compilateur cherchent la classe selon son package : `fr.b1` impose le dossier `fr/b1/`. Python n'impose pas de `package` déclaré dans le fichier, la structure des dossiers suffit.

**Q14.** (à vérifier) `package com.google.gson does not exist` à la compilation. En Python, sans `requests`, l'erreur `ModuleNotFoundError` n'apparaît qu'à l'exécution, au moment de l'import.

**Q15.** `release version 25 not supported` avec le JDK 21. La ligne fautive : `<maven.compiler.release>25</maven.compiler.release>`.

**Q16.** `JAVA_HOME` indique à Maven et aux outils quel JDK utiliser. `$env:` / `export` ne modifient que l'environnement du terminal courant, qui disparaît à sa fermeture.

**Q17.** Compatibilité, coût et risque d'une migration, dépendances non compatibles, tests à refaire, support long terme (LTS) déjà suffisant.

**Q18.** `py -3.12 -m venv .venv` (Windows) ou `pyenv` pour choisir la version. Un `.venv` conserve la version de Python avec laquelle il a été créé.

## Synthèse Python / Java

| Critère | Python | Java |
|---|---|---|
| Exécution | Interprété | Compilé en bytecode puis JVM |
| Lancer le programme | `python script.py` | `javac` + `java`, ou `mvn exec:java` |
| Typage (vérifié quand ?) | À l'exécution | À la compilation |
| Outil de dépendances | venv + pip | Maven |
| Fichier de dépendances | requirements.txt | pom.xml |
| Stockage des bibliothèques | `.venv` par projet | `~/.m2` partagé |
| Version du langage par projet | py launcher / pyenv / venv | JAVA_HOME / SDKMAN |
| Dossier généré à ignorer | `__pycache__/`, `.venv/` | `target/` |
| Lignes de `moyenne` | ~3 | ~10 |

**Q19.** Compilé : plus rapide et erreurs détectées tôt, mais cycle plus long. Interprété : lancement immédiat et souple, mais plus lent et erreurs découvertes tard.

**Q20.** La JVM (bytecode portable). Il faut installer un JRE ou JDK sur la machine cible.

**Q21.** Sur une application de 50 000 lignes : détecter tôt les erreurs de type évite des bugs cachés dans du code rarement exécuté ; sur 20 lignes, on les voit vite.

**Q22.** Renommage de fichiers : Python (script rapide). Android : Java/Kotlin. Analyse de données : Python (pandas). Serveur de banque : Java (robustesse, typage, écosystème).

**Q23.** Git, SSH, VS Code, le terminal sont identiques : ces outils sont indépendants du langage.
