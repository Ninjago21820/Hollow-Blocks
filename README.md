English | Français

# 📖 Wiki: Modpack Creator Configuration Guide

This mod is a **Client-Only** mod (installed on the client side only; it does not need to be installed on the server). It allows you to make certain vanilla or custom blocks non-opaque to properly display complex 3D models (hollowed-out blocks, cages, grates) without hiding the faces of adjacent blocks (*culling*) and with proper light propagation.

---

## 🛠️ Installation in a Modpack

1. Download the `.jar` file corresponding to your mod loader (**Fabric** or **NeoForge**).
2. Place the file into your modpack's `mods/` directory.
3. If you are using Fabric, ensure you also include **Fabric API**.

---

## ⚙️ Configuration via Resource Pack

The mod does not use a configuration file in the `config/` folder. Declaring hollow blocks is done **directly inside a Resource Pack** (for example, included via *Open Loader* or bundled within the modpack's default resource pack).

### 1. File Location

Inside your Resource Pack, create a JSON file at the following location:
`assets/<namespace>/hollow_blocks.json`

*(Examples: `assets/minecraft/hollow_blocks.json` or `assets/my_modpack/hollow_blocks.json`)*

### 2. JSON Structure

The file consists of a JSON object mapping the block ID (`namespace:block_id`) to its render attribute (`solid`, `partial`, or `transparent`).

```json
{
  "minecraft:iron_block": "partial",
  "minecraft:diamond_block": "transparent",
  "minecraft:stone": "solid"
}

```

---

## 💡 Render Attributes Breakdown

| Attribute | Culling (Neighboring Faces) | Light Propagation | Use Case |
| --- | --- | --- | --- |
| **`solid`** | Enabled (Hides faces) | Blocked | Standard vanilla behavior (full opaque blocks). |
| **`partial`** | Disabled (Renders faces) | Passes through | Models with small openings, grates, or hollow shapes. |
| **`transparent`** | Disabled (Renders faces) | Passes through | Glass blocks, open cages, or highly detailed, airy models. |

---

## ❓ FAQ & Compatibility

* **Does this mod need to be installed on the server?**
No, it is strictly **Client-Only**. Players can join any vanilla or modded server with this mod installed on their end.
* **Is it compatible with Sodium / Iris / Embeddium?**
Yes, the mod modifies occlusion properties at the `BlockStateBase` level, making it compatible with most rendering optimization mods.


# ________________________________________________________________________________________________________________________________________________________


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
