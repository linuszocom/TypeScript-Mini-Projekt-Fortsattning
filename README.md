# Uppgift: Fortsätt bygga på erat projekt

Idag är målet att fortsätta jobba på erat projekt. Ni ska använda TypeScript för att bygga upp och styra ert användargränssnitt baserat på data. Oavsett om ni bygger en webbshop, en att-göra-lista eller ett spel, är logiken densamma.

---

## Kravlista (Checklista)

Projektet ska innehålla och använda följande metoder.

- [ ] **Hämta element**
  Använd `document.querySelector()` eller `document.getElementById()` för att hitta behållare (containers) i din HTML där innehållet ska hamna.

- [ ] **Skapa element**
  Använd `document.createElement()` för att skapa nya HTML-taggar (t.ex. `div`, `li`, `article`, `button`) via koden.

- [ ] **Ändra innehåll**
  Använd `.textContent` för att fylla dina nya element med text (t.ex. namn, rubriker, beskrivningar).

- [ ] **Styla med klasser**
  Använd `.classList.add()` för att ge dina skapade element rätt CSS-klasser så att de får rätt utseende.

- [ ] **Montera (Rendera)**
  Använd `.appendChild()` eller `.append()` för att faktiskt lägga till dina nya element på sidan så att de syns.

- [ ] **Interaktion**
  Skapa minst en `.addEventListener()` som reagerar på användaren (t.ex. vid klick på en knapp/kort eller input i ett fält).

---

## Arbetsflöde: Hur du ska tänka

När du ska skapa innehåll dynamiskt, följ denna mentala checklista för varje sak du vill skapa:

1.  **Hitta platsen:** Vart ska elementet bo? (Hämta föräldern från HTML).
2.  **Skapa elementet:** Gör ett nytt, tomt element i minnet.
3.  **Fyll det:** Ge elementet text eller bilder.
4.  **Designa det:** Ge elementet en CSS-klass.
5.  **Montera det:** Skicka ut elementet till webbläsaren (append).

---

## Tips för att komma igång

### 1. Kommentera ut, radera inte
Istället för att radera din gamla HTML direkt (om det är så att du vill göra om efter dagens föreläsning), kommentera ut den . Då har du kvar den som en mall ("fusklapp") medan du skriver din TypeScript-kod.

### 2. Börja med en array
Har du ingen data än? Skapa en enkel lista i koden för att testa din loop:

```typescript
const myItems = ["Objekt 1", "Objekt 2", "Objekt 3"];

myItems.forEach((item) => {
  // Din kod för att skapa element här...
});
```

## Idétorka? Välj ett av dessa spår!

Om du inte vet vad du ska bygga, eller om du vill fortsätta på det vi gjort under lektionerna, välj ett av dessa spår:

### Spår 1: "Musikspelaren" (Fortsätt på demon)
För dig som har hängt med på lektionerna och vill bygga klart spelaren vi påbörjade.
* **Data:** Använd `playlist`-arrayen (låtlista) som vi tittade på.
* **Element:** Ta bort dina hårdkodade `<article>`-taggar i HTML och skriv en loop som skapar upp en grid av låtar med `document.createElement` istället.
* **Interaktion:** Koppla ihop listan med spelaren. När man klickar på ett kort i listan ska den "Stora spelaren" uppdateras med rätt titel, artist och omslagsbild.

### Spår 2: "Att-göra-listan" (The To-Do List)
En klassiker av en anledning. Bygg en lista med saker som ska göras.
* **Data:** En array med texter: `["Handla mjölk", "Gå ut med hunden", "Koda JS"]`.
* **Element:** Skapa `<li>` element för varje sak.
* **Interaktion:** När man klickar på en sak ändras stilen (t.ex. genomstruken text) för att visa att den är klar.

### Spår 3: "Mini-Butiken" (Product Cards)
Bygg en enkel produktsida för en webbshop (skor, växter, eller datordelar).
* **Data:** En array med objekt: `{ name: "Kaktus", price: 99, category: "Växt" }`.
* **Element:** Skapa "kort" (`div` eller `article`) som visar namn och pris.
* **Interaktion:** En "Köp"-knapp på varje kort. När man klickar loggas "Du köpte [Varan]!" i konsolen, eller så uppdateras en varukorgs-räknare på sidan.

### Spår 4: "Teamet" (Kontaktlista)
Bygg en "Om oss"-sida för ett företag.
* **Data:** En lista på anställda: `{ name: "Anna Andersson", role: "VD", email: "anna@company.com" }`.
* **Element:** Skapa profilkort med namn och titel.
* **Interaktion:** En knapp med texten "Kontakta". När man klickar på den visas personens email-adress (som var dold från början).

Implementera sedan dom olika sakerna från kravlistan.
Lycka till!

