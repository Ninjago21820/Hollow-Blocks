# 📖 Wiki : Guide de configuration pour Modpacks

Ce mod est un mod **Client-Only** (installé uniquement sur le client, pas besoin de l'avoir côté serveur). Il permet de rendre certains blocs vanilla ou personnalisés non-opaques pour afficher correctement les modèles 3D complexes (blocs creux, cages, grilles) sans masquer les faces des blocs voisins et en gérant la lumière.

---

## 🛠️ Installation dans un Modpack

1. Téléchargez le fichier `.jar` correspondant à votre loader (**Fabric** ou **NeoForge**).
2. Placez le fichier dans le dossier `mods/` de votre modpack.
3. Si vous utilisez Fabric, assurez-vous de d'inclure **Fabric API**.

---

## ⚙️ Configuration via Resource Pack

Le mod ne possède pas de fichier de configuration dans le dossier `config/`. La déclaration des blocs creux s'effectue **directement au sein d'un Resource Pack** (inclus par exemple via *Open Loader* ou dans le pack de ressources par défaut du modpack).

### 1. Emplacement du fichier

Dans votre Resource Pack, créez un fichier JSON à l'emplacement suivant :
`assets/<namespace>/hollow_blocks.json`

*(Exemple : `assets/minecraft/hollow_blocks.json` ou `assets/mon_modpack/hollow_blocks.json`)*

### 2. Structure du fichier JSON

Le fichier consiste en un objet JSON associant l'identifiant du bloc (`namespace:block_id`) à son attribut de rendu (`solid`, `partial`, ou `transparent`).

```json
{
  "minecraft:iron_block": "partial",
  "minecraft:diamond_block": "transparent",
  "minecraft:stone": "solid"
}

```

---

## 💡 Signification des attributs de rendu

| Attribut | Culling (Faces voisines) | Propagation de la lumière | Cas d'utilisation |
| --- | --- | --- | --- |
| **`solid`** | Actif (Masque les faces) | Bloquée | Comportement vanilla standard (blocs pleins). |
| **`partial`** | Désactivé (Affiche les faces) | Traverse le bloc | Modèles avec de petites ouvertures, grilles ou creux. |
| **`transparent`** | Désactivé (Affiche les faces) | Traverse le bloc | Blocs en verre, cages ouvertes ou modèles très aérés. |

---

## ❓ FAQ & Compatibilité

* **Le mod doit-il être installé sur le serveur ?**
Non, c'est un mod strictly **Client-Only**. Les joueurs peuvent se connecter à n'importe quel serveur vanilla ou moddé.
* **Est-ce compatible avec Sodium / Iris / Embeddium ?**
Oui, le mod altère les propriétés d'occlusion au niveau du `BlockStateBase`, ce qui s'intègre avec la plupart des moteurs de rendu d'optimisation.
