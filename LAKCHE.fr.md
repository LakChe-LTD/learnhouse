# LAKCHE Academy

[English](LAKCHE.md) · **Français**

Ce dépôt est le fork par LakChe LLC de [LearnHouse](https://github.com/learnhouse/learnhouse), la plateforme d'apprentissage open source qui fait tourner **LAKCHE Academy** (academy.lakche.com, [LC-51](https://lakchellc.atlassian.net/browse/LC-51)). Tout ce qu'il contient, sauf `LAKCHE.md`, `LAKCHE.fr.md`, `AGENTS.md`, `CLAUDE.md` et le bandeau en tête du `README.md`, est le LearnHouse d'origine, dont le `README.md` décrit le code.

> **Ce dépôt est public.** Ne commitez jamais d'identifiant, de clé d'API, d'adresse de serveur, de chemin personnel, ni de document qui en contient. Le runbook de l'Academy vit sur Confluence, dans l'espace LA ([LA-ENG-LMS-001, brouillon](https://lakchellc.atlassian.net/wiki/spaces/LA/pages/119341066)), et les valeurs uniquement dans le `.env` de l'instance et le gestionnaire de mots de passe.

## Comment tourne l'Academy

- **L'image officielle de LearnHouse, installée et pilotée avec la CLI officielle** (`npx learnhouse@latest setup`, puis `start`, `stop`, `update`, `logs`, `backup` et `doctor`). L'Academy n'est pas construite depuis ce fork.
- **L'identité visuelle est de la configuration**, réglée dans Organisation → Paramètres et stockée en base, si bien que les mises à jour ne l'écrasent jamais ([LC-52](https://lakchellc.atlassian.net/browse/LC-52)). Il en va de même pour la page d'accueil, les cours, les groupes d'utilisateurs et les certificats.
- **Édition open source uniquement.** Ce fork n'a pas de dossier entreprise : il fait tourner tout, sauf le SSO, les journaux d'audit, les paiements, l'analytique avancée et SCORM, qui relèvent de la licence Enterprise distincte de LearnHouse.

## Garder le fork léger

1. **Ce fork reste un miroir non modifié de LearnHouse**, plus les fichiers LakChe cités plus haut. On fait évoluer l'Academy par la configuration d'abord.
2. **Toute modification du code exige un ticket et une décision du CTO.** LearnHouse est sous AGPL-3.0 : si l'Academy fait un jour tourner du code modifié, ses utilisateurs ont droit à ce code. Il est alors publié ici, sur une branche au nom du ticket.
3. **Les mises à jour viennent des versions de LearnHouse.** Synchronisez `dev` avec LearnHouse par une pull request, puis mettez l'instance à jour avec `npx learnhouse update`, selon le runbook, après une sauvegarde.
4. **Gardez `LICENSE` et toutes les mentions de copyright.** Le retrait du badge « Made with LearnHouse » reste à décider (D7, [LC-51](https://lakchellc.atlassian.net/browse/LC-51)).

## Développer en local

```bash
npx learnhouse dev
```

Cette commande lance PostgreSQL et Redis, puis l'API (`apps/api`, FastAPI), l'application web (`apps/web`, Next.js) et le serveur de collaboration (`apps/collab`). La création des cours peut commencer sur une instance locale et être importée ensuite (runbook, étape 8.6). Voir [apps/cli/README.md](apps/cli/README.md) pour toutes les commandes.

## Sécurité

- Signalez une faille de l'instance de l'Academy de LakChe en privé au CISO.
- Signalez une faille de LearnHouse lui-même à ses mainteneurs, comme l'indique la section Security de leur README.
- L'inscription publique reste fermée tant que les conditions d'utilisation et la politique de confidentialité de l'Academy ne sont pas en ligne (D2, [LC-51](https://lakchellc.atlassian.net/browse/LC-51)).

## Travailler dans ce dépôt

1. **Partez d'un ticket Jira** du projet LAKCHE. Un ticket par branche et par pull request, moins de 400 lignes modifiées, relue et fusionnée par quelqu'un d'autre que l'auteur.
2. **Créez la branche** sous la forme `{type}/{vous}/{LC-nn-nom-court}` et écrivez des Conventional Commits.
3. **Lisez [AGENTS.md](AGENTS.md)** avant toute modification, avec ou sans agent d'IA.
4. **Secrets :** désignez-les par leur nom uniquement. Si vous en trouvez un dans le dépôt ou son historique, arrêtez-vous et prévenez le Tech Lead et le CISO. Il est renouvelé, pas seulement supprimé.
5. **Les consignes orales** qui modifient un ticket y sont notées le jour même, en une ligne, par la personne qui les a reçues ([règle](https://lakchellc.atlassian.net/wiki/pages/viewpage.action?pageId=106856449)).

## Liens

| Quoi | Où |
|---|---|
| Déploiement, vérification de licence et mises à jour | [LC-51](https://lakchellc.atlassian.net/browse/LC-51) |
| Identité visuelle, structure des cours, lien depuis lakche.com | [LC-52](https://lakchellc.atlassian.net/browse/LC-52) |
| Runbook (EN) et guide de mise en œuvre (FR), brouillons | [LA-ENG-LMS-001](https://lakchellc.atlassian.net/wiki/spaces/LA/pages/119341066), [guide FR](https://lakchellc.atlassian.net/wiki/spaces/LA/pages/119308293) |
| Cette documentation | [LC-57](https://lakchellc.atlassian.net/browse/LC-57) |
| Definition of Done | [LAKCHE-ENG-GOV-001 §3.4](https://lakchellc.atlassian.net/wiki/pages/viewpage.action?pageId=38928386) |
