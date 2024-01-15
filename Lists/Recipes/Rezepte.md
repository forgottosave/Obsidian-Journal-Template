![[Rezeptbuch.png]]

# Verzeichnis
1. **[[Rezepte#Hauptgerichte|Hauptgerichte]]**
	1.1. [[Rezepte#Suppen|Suppen]]
	1.1. [[Rezepte#Fleisch|Fleisch]]
	1.2. [[Rezepte#Vegetarisch|Vegetarisch]]
	1.3. [[Rezepte#Fisch|Fisch]]
	
2. **[[Rezepte#Beilagen|Beilagen]]**

---



# Hauptgerichte
### Suppen
```dataview
TABLE WITHOUT ID file.link as "Gericht", Bild as "", Dauer + " min" as "Dauer", Zutaten as "Zutaten"
FROM "Lists/Recipes"
WHERE
	Dauer > 0 AND
	contains(Gang,"Hauptgericht") AND
	contains(tags,"suppe")
```


### Fleisch
```dataview
TABLE WITHOUT ID file.link as "Gericht", Bild as "", Dauer + " min" as "Dauer", Zutaten as "Zutaten"
FROM "Lists/Recipes"
WHERE
	Dauer > 0 AND
	contains(Gang,"Hauptgericht") AND
	contains(tags,"fleisch")
```


### Vegetarisch
```dataview
TABLE WITHOUT ID file.link as "Gericht", Bild as "", Dauer + " min" as "Dauer", Zutaten as "Zutaten"
FROM "Lists/Recipes"
WHERE
	Dauer > 0 AND
	contains(Gang,"Hauptgericht") AND
	contains(tags,"vegetarisch")
```


### Fisch
```dataview
TABLE WITHOUT ID file.link as "Gericht", Bild as "", Dauer + " min" as "Dauer", Zutaten as "Zutaten"
FROM "Lists/Recipes"
WHERE
	Dauer > 0 AND
	contains(Gang,"Hauptgericht") AND
	contains(tags,"fisch")
```


---



# Beilagen
