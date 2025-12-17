## Allies
```dataview
TABLE WITHOUT ID
file.link AS Name, AKA, Affiliations, Province, Family, Clan 
FROM #NPC 
WHERE sentiment = "Ally"
```
## Enemies
```dataview
TABLE WITHOUT ID
file.link AS Name,  AKA, Affiliations, Province, Family, Clan 
FROM #NPC 
WHERE sentiment = "Enemy"
```

## Neutral
```dataview
TABLE WITHOUT ID
file.link AS Name,  AKA, Affiliations, Province, Family, Clan 
FROM #NPC 
WHERE sentiment = "Neutral"
```