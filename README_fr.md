<div align="center">

# 🤖 Omnibot

### Infrastructure de Navigateur pour Agents IA

[![Version](https://img.shields.io/badge/version-2.4.0-blue?style=flat-square)](./SKILL.md)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey?style=flat-square)]()

[![SkillHub](https://img.shields.io/badge/SkillHub-omnibot-00A8E0?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdCb3g9IjAgMCAxNiAxNiIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48cGF0aCBkPSJNOCAwTDAgNFYxMkw4IDE2TDE2IDEyVjRMOCAwWiIgZmlsbD0id2hpdGUiLz48L3N2Zz4=)](https://skillhub.cn/skills/omnibot)
[![ClawHub](https://img.shields.io/badge/ClawHub-omnibot--skills-FF6B35?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdCb3g9IjAgMCAxNiAxNiIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48cGF0aCBkPSJNOCAxQzQuMTMgMSAxIDQuMTMgMSA4QzEgMTEuODcgNC4xMyAxNSA4IDE1QzExLjg3IDE1IDE1IDExLjg3IDE1IDhDMTUgNC4xMyAxMS44NyAxIDggMVpNOCAzQzkuNjYgMyAxMSA0LjM0IDExIDZDMTEgNy42NiA5LjY2IDkgOCA5QzYuMzQgOSA1IDcuNjYgNSA2QzUgNC4zNCA2LjM0IDMgOCAzWiIgZmlsbD0id2hpdGUiLz48L3N2Zz4=)](https://clawhub.ai/dennisjcy/skills/omnibot-skills)

[![Chrome Web Store](https://img.shields.io/badge/Chrome%20Web%20Store-Extension%20de%20Navigateur-4285F4?style=flat-square&logo=google-chrome&logoColor=white)](https://chromewebstore.google.com/detail/fojlpefamkmjbboafmjkkaejohagbdgn)

**Connectez les agents IA à un vrai navigateur Chromium.**<br>
Lisez des pages. Cliquez sur des boutons. Remplissez des formulaires. Naviguez. Extrayez du contenu. Collectez des preuves.<br>
Tout via un démon local et une CLI — pas de hacks headless, pas de sélecteurs fragiles.

[Démarrage Rapide](#-démarrage-rapide) · [Comment Ça Marche](#-comment-ça-marche) · [Fonctionnalités](#-fonctionnalités) · [Documentation](#-documentation)

🌐 **[English](./README.md)** · **[中文](./README_zh.md)** · **[日本語](./README_ja.md)** · **[한국어](./README_ko.md)** · **[Español](./README_es.md)** · **[Deutsch](./README_de.md)**

</div>

---

## 🚀 Qu'est-ce qu'Omnibot ?

Omnibot comble le fossé entre les agents IA et le web réel. Il donne aux agents comme **Hermes**, **Claude Code**, **Codex**, **OpenCode** et autres la capacité de voir et d'interagir avec un navigateur Chromium vivant — de la même manière qu'un humain.

```
┌──────────────┐         ┌──────────────┐         ┌──────────────────┐
│   AI Agent   │ ──CLI──▶│  Omnibot     │ ──WS──▶ │  Chromium        │
│  (Hermes,    │         │  Démon       │         │  Extension       │
│   Claude...) │         │  :18765      │         │  (Vrai Navigateur)│
└──────────────┘         └──────────────┘         └──────────────────┘
```

Pas de Puppeteer. Pas de Playwright. Pas de navigateur headless qui prétend être réel.<br>
**Un vrai navigateur. De vrais cookies. De vraies extensions. De vraies sessions utilisateur.**

## 🎬 Démonstrations Vidéo

<table>
<tr>
<td width="50%" align="center" valign="top">

### Analyse de Compte Officiel WeChat
**Hermes analyse automatiquement les données et tendances WeChat**

[![Analyse WeChat](https://img.youtube.com/vi/xZ-_0TInCRE/maxresdefault.jpg)](https://youtu.be/xZ-_0TInCRE)

*L'agent Hermes se connecte automatiquement au backend du Compte Officiel WeChat, extrait la croissance des utilisateurs, les lectures d'articles, la démographie des utilisateurs et génère un rapport d'analyse de données complet.*

</td>
<td width="50%" align="center" valign="top">

### Agrégateur de Nouvelles IA sur X (Twitter)
**Hermes parcourt X automatiquement pour les dernières nouvelles IA**

[![Nouvelles IA sur X](https://img.youtube.com/vi/PknnOhAE6bI/maxresdefault.jpg)](https://youtu.be/PknnOhAE6bI)

*L'agent Hermes parcourt automatiquement X (Twitter), recherche et filtre les dernières nouvelles IA, et les organise en un briefing structuré.*

</td>
</tr>
<tr>
<td width="50%" align="center" valign="top">

### Analyse de Documents Judiciaires
**Hermes recherche et analyse des verdicts d'homicides**

[![Analyse Judiciaire](https://img.youtube.com/vi/PQQNDbzgXgQ/maxresdefault.jpg)](https://youtu.be/PQQNDbzgXgQ)

*L'agent Hermes recherche dans les dossiers judiciaires des cas d'homicide, lit 8 dossiers de cas complets et génère un rapport d'analyse complet incluant des profils de délinquants, une analyse des motifs et des schémas de criminalité.*

</td>
<td width="50%" align="center" valign="top">

### Publication Automatique sur Toutiao
**Hermes publie automatiquement des articles sur Toutiao**

[![Publication Toutiao](https://img.youtube.com/vi/elUxHLp1C4Q/maxresdefault.jpg)](https://youtu.be/elUxHLp1C4Q)

*L'agent Hermes se connecte automatiquement à Toutiao, remplit le titre, le texte du corps, insère des images, configure la couverture et les revenus publicitaires, prévisualise et publie l'article en un clic.*

</td>
</tr>
</table>

<div align="center">

**Plus de cas d'usage vous attendent !**

</div>

## ✨ Fonctionnalités

<table>
<tr>
<td width="50%" valign="top">

### 🔍 Observer
- Lit le contenu de page rendu comme du texte/Markdown propre
- Capture l'arbre d'accessibilité complet avec des références interactives
- Capture des captures d'écran de pages complètes ou de régions visuelles spécifiques
- Inspecte les logs de console, le trafic réseau et l'état du DOM

</td>
<td width="50%" valign="top">

### 🎯 Agir
- Clique sur des éléments par rôle sémantique, placeholder ou référence d'accessibilité
- Remplit des formulaires, sélectionne des options, coche des cases — avec dispatch d'événements
- Navigue entre les pages, gère les onglets et groupes d'onglets
- Glisse, défile, tape, appuie sur des touches — interaction humaine

</td>
</tr>
<tr>
<td width="50%" valign="top">

### ✅ Vérifier
- Attend des conditions : changements d'URL, visibilité d'éléments, apparition de texte
- Affirme l'état des éléments : activé, visible, coché, valeur
- Capture les logs réseau et les preuves d'API
- Vérification multi-étapes avec boucles observer → agir → vérifier

</td>
<td width="50%" valign="top">

### 🛡️ Fiable
- Isolation de flux de travail par token de session
- Commandes ciblées par onglet — pas de mutations croisées accidentelles
- Chaîne de fallback de 7 niveaux du sémantique au CDP brut
- Gardes anti-pattern intégrées et règles de sécurité

</td>
</tr>
</table>

## ⚡ Démarrage Rapide

### 1. Installer Omnibot

```bash
pip install omnibot
```

### 2. Démarrer le démon

```bash
omnibot daemon run
```

### 3. Charger l'extension Chromium

Ouvrez Chrome ou Edge avec l'extension Omnibot installée. Gardez au moins un onglet HTTP/HTTPS ouvert.

### 4. Vérifier la connexion

```bash
omnibot doctor
omnibot tabs
```

### 5. Donner le skill à votre agent

Placez [`SKILL.md`](./SKILL.md) dans le répertoire de skills de votre agent. C'est tout — votre agent a maintenant des super-pouvoirs de navigateur.

## 🔄 Comment Ça Marche

Chaque opération de navigateur suit une boucle disciplinée :

```
  ┌──────────┐      ┌──────────┐      ┌──────────┐
  │ Observer │ ───▶ │  Agir    │ ───▶ │ Vérifier │──┐
  │          │      │ (une fois)│     │          │  │
  └──────────┘      └──────────┘      └──────────┘  │
       ▲                                              │
       └──────────── réessayer avec fallback ─────────┘
```

1. **Observer** — capture la page, lit le contenu, vérifie l'état actuel
2. **Agir** — effectue une opération en utilisant le meilleur pattern disponible
3. **Vérifier** — confirme le changement d'état attendu avec des preuves

Si la vérification échoue, l'agent ré-observe et essaie le niveau de fallback suivant. Pas de tentatives aveugles. Pas de devinettes.

## 🧩 Routeur de Commandes Natives

Omnibot choisit toujours la commande native la plus étroite pour le travail :

| Intention | Commande Native | Pas Ceci |
|-----------|----------------|----------|
| Lire le contenu de page | `read`, `get text` | ~~`execute-js`~~ |
| Cliquer sur un bouton | `find --action click`, `click @eN` | ~~`querySelector().click()`~~ |
| Remplir un formulaire | `fill`, `type` | ~~`element.value = "..."`~~ |
| Attendre l'état | `wait` | ~~`sleep 3`~~ |
| Défiler | `scroll`, `scrollintoview` | ~~`window.scrollTo()`~~ |

**Natif d'abord. JavaScript est un fallback, pas un raccourci.**

## 🏗️ Architecture

```
Agent Skill (SKILL.md)
    │
    ▼
omnibot CLI  ──────────────────────────────┐
    │                                       │
    ▼                                       ▼
Démon Local (:18765)                Extension Chromium
    │                                       │
    ├── Gestion de sessions                 ├── Accès DOM
    ├── Routage de commandes                ├── Arbre d'accessibilité
    ├── Suivi d'onglets                     ├── Interception réseau
    └── Isolation de flux de travail        └── Détection de régions visuelles
```

**Principes de conception clés :**
- **Fiabilité > Convenance** — chaque action est vérifiée
- **État Explicite > État Implicite** — pas de suppositions cachées
- **Pattern > Commande** — commencez par la tâche, pas l'API
- **Le fallback est autorisé, mais jamais en premier**

## 📚 Documentation

| Ressource | Description |
|-----------|-------------|
| [SKILL.md](./SKILL.md) | Spécification complète d'exécution d'agent |
| [Référence des Commandes](./references/command-reference.md) | Recherche complète de commandes CLI |
| [Patterns d'Opération](./references/operation-patterns.md) | Lire, cliquer, remplir, défiler, naviguer, attendre, extraire, lot |
| [Anti-Patterns](./references/anti-patterns.md) | Erreurs courantes et comment les éviter |
| [Débogage et Preuves](./references/debugging-and-evidence.md) | Captures d'écran, logs réseau, trace, enregistrement/lecture |
| [Sessions et Onglets](./references/session-and-tabs.md) | Isolation de flux de travail et ciblage d'onglets |
| [Opérations de Fallback](./references/fallback-operations.md) | Chaîne de fallback de 7 niveaux expliquée |

## 🤝 Agents Compatibles

Omnibot fonctionne avec tout système d'agent qui peut exécuter des commandes CLI :

- 🧠 **Hermes** — intégration native
- 🟠 **Claude Code** — via fichier de skill
- 📦 **Codex** — via fichier de skill
- 🔓 **OpenCode** — via fichier de skill
- 🔧 **Tout agent compatible CLI** — via commandes `omnibot`

## 📋 Exemple de Flux de Travail

```bash
# Définir le contexte de flux de travail
export OMNIBOT_SESSION_TOKEN=research

# Ouvrir un nouvel onglet
omnibot open "https://github.com"

# Capturer la page avec des références interactives
omnibot snapshot -i --tab-id $TAB_ID

# Cliquer sur la boîte de recherche et taper
omnibot find placeholder "Search GitHub" --action type \
  --action-value "omnibot" --tab-id $TAB_ID

# Appuyer sur Entrée
omnibot press Enter --tab-id $TAB_ID

# Attendre les résultats
omnibot wait --text "repositories" --tab-id $TAB_ID

# Lire les résultats
omnibot read --tab-id $TAB_ID
```

## 📄 Licence

Propriétaire. Voir LICENSE pour les détails.

---

<div align="center">

**Construit pour les agents qui ont besoin de voir le web — pas juste le récupérer.**

[⭐ Étoile sur GitHub](https://github.com/DennisJcy/Omnibot-skills) · [📖 Lire la Spécification de Skill](./SKILL.md)

</div>
