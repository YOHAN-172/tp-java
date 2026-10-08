# TP Java : préparer son environnement

## Installation (macOS)

1. Homebrew : https://brew.sh
2. JDK 21 et 25 (Temurin) : `brew install --cask temurin@21 temurin@25`
3. Maven : `brew install maven`
4. VS Code + Extension Pack for Java

Vérification : `java -version`, `javac -version`, `mvn -version`.

## Changer de JDK par projet

- Manuellement : `export JAVA_HOME=$(/usr/libexec/java_home -v 21)` puis `export PATH="$JAVA_HOME/bin:$PATH"` (valable dans le terminal courant uniquement).
- Avec SDKMAN : `sdk env init` crée `.sdkmanrc` (`java=21.0.12-tem` ou `java=25.0.4-tem`), puis `sdk env` à l'entrée du dossier.

## Projets

- `tp-env-java` : Maven + Gson (Java 21)
- `projet-java21` : même code, JDK 21
- `projet-java25` : `Main.java` simplifié, JDK 25
