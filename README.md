# exercise-mongodb-queries

## Importiere den Datensatz "people.json"
* erstelle mit Compass eine neue Datenbank **test** mit einer Collection **people**
* importiere dann die Datei

## Daten untersuchen
Schaue dir die Daten gründlich an.

## Daten finden
Schreibe ein Query für jede Aufgabe.  
Das fertige Query kannst du hier als Antwort einfügen.  
Hilfe:
[MongoDB Query](https://docs.mongodb.com/manual/tutorial/query-documents/)  
[MongoDB Operatoren](https://docs.mongodb.com/manual/reference/operator/query/#projection-operators)

### 1. Finde Angelo
Finde nur die Person mit dem Namen **Angelo**

Antwort:
```json
{name: "Angelo"}
```

### 2. Finde Alle mit A im Namen
Finde allePersonen mit einem "A" im Namen

Antwort:
```json
{name: /A/i}  
{name: /[aA]/}
```

### 3. Finde alle mit genau 25 Jahren
Finde alle Personen, deren Alter genau **25** ist.

Antwort:
```json
{age: 25}
```

### 4. Finde alle im Alter von 20 bis 30
Finde alle Personen, deren Alter zwischen 20 und 30 Jahren liegt (inklusive 20 und 30)

Antwort:
```json
{age: { $gte: 20, $lte: 30 } }
```

### 5. Finde alle unter 20
Finde alle Personen, deren Alter unter **20** ist.

Antwort:
```json
{ age: { $lt: 20 } }
```

### 6. Finde Luke und Abdu
Finde nur die zwei Personen mit den Namen, **Luke** und **Abdu**.

Antwort:
```json
{ name: {$in: ["Luke", "Abdu"]}}
```

### 7. Finde alle mit Haustier
Finde alle (3) Personen mit einem oder mehreren Haustieren.
(Achtung Schwer!)

Antwort:
```json
{ pets: { $not: { $size: 0 }} }   // alle Arrays un pets die nicht Länge 0 haben
{ "pets.0": { $exists: true }  }  // alle Arrays bei denen der Index 0 existiert
```

### 8. Finde die Person mit der Katze "Zoey"
Finde genau eine Person, mit einer Katze, die den Namen **Zoey** hat.
(Achtung Schwer)

Antwort:
```json
{ "pets.name": "Zoey" } 
{ pets: { $elemMatch: { name: "Zoey", kind: "Cat" } } } //Hier wird auch geprüft ob es sich um eine Katze handelt
```

### 9. Finde alle die Football mögen
Finde alle Personen, die Football (**football**) in der Liste ihrerer Hobbies haben.

Antwort:
```json
{ hobbies: "football" }
```

### 10. Finde alle die Filme mögen und Über 20 sind
Finde alle Personen, die Filme (**movies**) in der Liste ihrerer Hobbies haben **und** aälter sind als **20** Jahre.

Antwort:
```json
{ $and: [ {hobbies: "movies"}, {age: { $gt: 20 }} ] } 
```
