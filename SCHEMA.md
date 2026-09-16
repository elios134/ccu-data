# Schéma `ccu-index.json`

```jsonc
{
  "schemaVersion": 1,
  "generatedAt": "2026-09-16T17:41:57Z",   // ISO-8601 UTC
  "source": "sc-fleet-manager-v2",
  "ships":    [ { "shipId": 123, "name": "Aurora MR" } ],
  "skus":     [ { "skuId": 456, "shipId": 123, "priceCents": 2500,
                  "available": true, "unlimitedStock": true, "availableStock": null } ],
  "upgrades": [ { "fromShipId": 123, "toSkuId": 789, "upgradePriceCents": 1500 } ]
}
```

- **ships** → table `RsiShipName` (jointure nom canonique).
- **skus** → table `CcuSku` (cibles achetables). `available:false` = plus en vente (gardé).
- **upgrades** → table `CcuUpgrade` (arête `fromShipId → toSkuId`). `toSkuId` référence
  toujours un `skus[].skuId` présent (intégrité garantie à la génération).

Merge **no-delete** : une entrée n'est jamais supprimée ; disparue du store → `available:false`.
