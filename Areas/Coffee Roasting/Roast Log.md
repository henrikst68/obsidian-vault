---
tags:
  - coffee-roasting
  - log
---
# Roast Log

Requires the **Dataview** community plugin. Rows come from the properties in each note in `Sessions/`.

## All roasts
```dataview
TABLE WITHOUT ID
  file.link AS "Roast",
  date AS "Date",
  bean AS "Bean",
  green_g AS "Green g",
  weight_loss_pct AS "Loss %",
  first_crack_time AS "1C",
  drop_time AS "Drop",
  dtr_pct AS "DTR %",
  variable_changed AS "Changed",
  score AS "Score"
FROM "Areas/Coffee Roasting/Sessions"
SORT date DESC
```

## Result photos
```dataview
TABLE WITHOUT ID
  file.link AS "Roast",
  bean AS "Bean",
  roast_level AS "Level",
  embed(link(photo)) AS "Photo"
FROM "Areas/Coffee Roasting/Sessions"
WHERE photo
SORT date DESC
```

## Best per bean
```dataview
TABLE WITHOUT ID
  bean AS "Bean",
  max(rows.score) AS "Best score",
  length(rows) AS "Roasts"
FROM "Areas/Coffee Roasting/Sessions"
GROUP BY bean
```
