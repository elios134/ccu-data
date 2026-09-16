# ccu-data

Catalogue CCU (Cross-Chassis Upgrade) partagé pour **SC Fleet Manager v2**.

`ccu-index.json` est la **source de vérité en ligne** de l'onglet CCU de l'app : il liste
tous les vaisseaux, SKU et arêtes d'upgrade du store RSI, y compris **les vaisseaux qui ne
sont plus en vente** (`available: false`, dernier prix connu conservé) afin qu'ils restent
planifiables.

- Consommé par l'app via `sync_ccu_from_index` (fetch de `ccu-index.json` sur la branche `main`).
- Régénéré ~1×/semaine par `tools/ccu_publish.py` (repo sc-fleet-manager-v2) — merge **no-delete**.
- Schéma : voir [SCHEMA.md](SCHEMA.md).

Généré depuis la base de l'app ; aucune donnée personnelle (uniquement le catalogue public du store).
