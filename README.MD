# Environnement C++ alternatif (Visual Studio Code) pour macOS

## 1. Installer un compilateur et les outils nécessaires
  Ouvrez une fenêtre terminal soit via Spotlight soit en cherchant directement l’application Terminal dans le dossier Applications.
  Taper 
```
xcode-select --install
```
  Vous avez à présent installé tous les compilateurs et outils nécessaires pour écire et compiler du code C++ sur macOS. Cependant, il est possible que dans le futur vous ayez besoin d'installer d'autres outils comme des bibliothèques, des debuggers, etc. Pour ce faire, le plus simple est de passer par un gestionnaire de paquets :  je recommande [Homebrew](homebrew.md).

## 2. Installer l'éditeur de texte Visual Studio Code

### Un peu de terminologie
À mon sens, Visual Studio Code (ou VSCode) est un simple **éditeur de texte** (*text editor* en anglais), au même titre que Geany. Ce n'est pas un **environnement de développement** (*IDE* en anglais) à proprement parler car il ne comprend aucun compilateur ou outil nécessaire pour éxecuter le code qu'on écrit, l'analyser et le débugger. VSCode ne permet (seul) que d'écrire des fichiers de code et d'éventuellement gérer ces fichiers (grâce à git ou un autre gestionnaire de version).

### Installation
Si vous avez installé Homebrew vous pouvez tout simplement entrer
```
brew install --cask visual-studio-code
```
dans un terminal pour installer l'application. Sinon, vous pouvez la télécharger à partir du [site officiel](https://code.visualstudio.com/).

Pour l'ouvrir, utliser Spotlight ou aller dans le dossier Applications.

## 3. Configuration
### Un mot sur le fonctionnement de VSCode
Lorsqu'on ouvre VSCode pour la première fois, aucun fichier ou dossier n'est ouvert. On peut ouvrir 
### On y va !
1. Télécharger l'extension C/C++
2. Modifier settings.json
3. Créer un dossier Developper et un dossier C++ (ATTENTION, jamais d'espace dans les noms de fichiers)

```json
{
    // Compilateur et standard C/C++
    "C_Cpp.default.compilerPath": "/usr/bin/clang++",
    "C_Cpp.default.cStandard": "c17",
    "C_Cpp.default.cppStandard": "c++17",
    // Configuration d'Intellisense, le programme d'auto-complétion de VSCode
    "C_Cpp.updateChannel": "Default",
    "C_Cpp.errorSquiggles": "Enabled",
    "C_Cpp.intelliSenseEngineFallback": "Enabled",
    "C_Cpp.intelliSenseEngine": "Default",
    "C_Cpp.default.intelliSenseMode": "clang-x64",

    // recherche des headers et bibliothèques
    "C_Cpp.default.includePath": [
        "${workspaceFolder}/**",
        "/usr/local/include/**"
    ],
    "C_Cpp.default.browse.path": [
        "/usr/local/lib",
        "/usr/local/include",
    ],
}
```

## 4. Écrire un premier programme

## 5. Aller plus loin

Autres extensions utiles :
- Thèmes comme [Monokai Pro](https://marketplace.visualstudio.com/items?itemName=monokai.theme-monokai-pro-vscode) (mon préféré), [Material Theme](https://marketplace.visualstudio.com/items?itemName=Equinusocio.vsc-material-theme), [Shades of Purple](https://marketplace.visualstudio.com/items?itemName=ahmadawais.shades-of-purple), ...
- 