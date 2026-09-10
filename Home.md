## Character Summaries
```dataview
table WITHOUT ID
file.name AS Name, Clan, Family, School, Class, Gender, Religion
from "The Party"
```

## NPCs

### Allies
```dataview
TABLE WITHOUT ID
file.link AS Name, status, Clan 
FROM #NPC 
WHERE sentiment = "Ally"
```

### Enemies
```dataview
TABLE WITHOUT ID
file.link AS Name, status, Clan 
FROM #NPC 
WHERE sentiment = "Enemy"
```

### Neutral
```dataview
TABLE WITHOUT ID
file.link AS Name, Clan 
FROM #NPC 
WHERE sentiment = "Neutral"
```

## Summaries
```dataview
TABLE WITHOUT ID 
file.link AS Session, date AS Date, summary AS Summary 
FROM "Sessions"
SORT date DESC
```
