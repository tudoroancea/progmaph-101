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
dans un terminal pour installer l'application. Sinon, vous pouvez la télécharger à partir du [site officiel de Microsoft](https://code.visualstudio.com/).

Pour l'ouvrir, utliser Spotlight ou aller dans le dossier Applications.

## 3. Configuration
### Un mot sur le fonctionnement de VSCode
Lorsqu'on ouvre VSCode pour la première fois, aucun fichier ou dossier n'est ouvert. Grâce à `Cmd+O` ou en allant dans l'onglet Fichier, on peut ouvrir un fichier ou un dossier. Ouvrir un fichier l'ouvre tout simplement et l'affiche. Ouvrir un dossier permet d'afficher à gauche dans le menu explorer le contenu du dossier et facilement créer des nouveaux fichiers ou sous-dossiers. Cela permet également de plus facilement ouvrir un dossier contenant un projet en particulier, et également d'ajouter des réglages propres à un certain dossier, qui vont être partagés par tous les fichiers cotenus à l'intérieur. Ces réglages sont contenus dans des fichiers au format JSON (extension `.json`), eux-mêmes contenus dans un dossier `.vscode` à la racine du fichier.
Ces réglages vont écraser les réglages globaux définis pour toute l'application (contenus dans un fichier `settings.json` placé dans les dossiers internes de VSCode).

Je recommande grandement de créer un dossier spécifique pour les programmes C++ (nommé par exemple `cxx`) que vous ouvrirez à chaque fois que vous aurez besoin d'écrire un programme. Pour le créer dans le dossier home de votre utilisateur  puis l'ouvrir, ouvrez un terminal et entrez:
```bash
cd ~
mkdir cxx
cd cxx
```
**Astuce** : pour ouvrir facilement un dossier ou un fichier dans VSCode depuis le terminal, vous pouvez ouvrir la Command Palette dans VSCode et chercher `Shell Command : Install 'code' command in PATH`. À présent vous pouvez ouvrir un dossier avec `code <nom>`. Exemple:
```bash
cd ~/cxx
code .
```

### Maintenant on attaque le C++ !
- Aller dans l'onglet Extensions (Cmd+X) et télécharger l'extension C/C++ de Microsoft
![C/C++ extension](images/c-c++-extension.png)
Cette extension contient la colorisation syntaxique pour les langages C et C++ ainsi que le nécessaire pour utiliser Intellisense, le programme d'auto-complétion de VSCode.

- Ouvrir la Command Palette (Cmd+P) et chercher `Preferences: Open Settings (JSON)`. Rajouter les lignes suivantes à l'intérieur des accolades:
```json
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
]
```


## 4. Écrire un premier programme
Une fois le dossier `cxx` ouvert dans VSCode, créer un nouveau fichier `hello-world.cpp` et écrivez :
```cpp
#include <iostream>

using namespace std;

int main() {
  cout << "Hello World !" << endl;
  return 0;
}
```
Pour éxecuter le programme nous allons créer une task dans `task.json`.
## 5. Aller plus loin

Autres extensions utiles :
- Thèmes comme [Monokai Pro](https://marketplace.visualstudio.com/items?itemName=monokai.theme-monokai-pro-vscode) (mon préféré), [Material Theme](https://marketplace.visualstudio.com/items?itemName=Equinusocio.vsc-material-theme), [Shades of Purple](https://marketplace.visualstudio.com/items?itemName=ahmadawais.shades-of-purple), ...
- 