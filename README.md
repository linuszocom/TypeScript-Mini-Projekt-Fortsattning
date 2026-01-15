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


## Dagens kod**
**index.html**
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="./style.css" />
    <link
      rel="stylesheet"
      href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@24,400,0,0"
    />
    <script type="module" src="./dist/index.js"></script>
    <title>Codeify Music</title>
  </head>

  <body>
    <header class="top-bar">
      <input
        type="text"
        id="search-input"
        placeholder="Sök efter låt"
        aria-label="Sök efter låt"
      />
    </header>
    <main id="song-list-container" class="song-grid"></main>

    <footer id="player-footer" class="player-card fixed-bottom">
      <div class="info-wrapper">
        <h2 id="song-title" class="song-title">Välj en låt</h2>
        <span id="song-artist" class="artist-name">...</span>
      </div>

      <div class="controls-wrapper">
        <button
          id="prev-btn"
          class="control-btn"
          aria-label="Spela föregående låt"
        >
          <span class="material-symbols-outlined">skip_previous</span>
        </button>

        <button
          id="play-btn"
          class="control-btn play-btn"
          aria-label="Spela eller pausa"
        >
          <span class="material-symbols-outlined">pause</span>
        </button>

        <button id="next-btn" class="control-btn" aria-label="Spela nästa låt">
          <span class="material-symbols-outlined">skip_next</span>
        </button>
      </div>
    </footer>
  </body>
</html>

```

**index.ts**
```
// Interfaces/Typer
interface Song {
  id: number;
  title: string;
  artist: string;
  durationInSeconds: number;
  album: Album;
}

interface Album {
  title: string;
  year: number;
  coverUrl?: string;
}

type PlayerStatus = "playing" | "paused" | "stopped";

const playlist: Song[] = [
  {
    id: 1,
    title: "Bohemian Rhapsody",
    artist: "Queen",
    durationInSeconds: 320,
    album: {
      title: "A night at the Opera",
      year: 1975,
      coverUrl: "https://example.com/queen.jpg",
    },
  },
  {
    id: 2,
    title: "Blinding Lights",
    artist: "The Weeknd",
    durationInSeconds: 200,
    album: {
      title: "After Hours",
      year: 2020,
      coverUrl: "https://example.com/weeknd.jpg",
    },
  },
  {
    id: 3,
    title: "Africa",
    artist: "Toto",
    durationInSeconds: 300,
    album: {
      title: "Toto IV",
      year: 1982,
    },
  },
  {
    id: 5,
    title: "Africa",
    artist: "Toto",
    durationInSeconds: 300,
    album: {
      title: "Toto IV",
      year: 1982,
    },
  },
  {
    id: 4,
    title: "Africa",
    artist: "Toto",
    durationInSeconds: 300,
    album: {
      title: "Toto IV",
      year: 1982,
    },
  },
  {
    id: 4,
    title: "Never Give You Up",
    artist: "Rick Astley",
    durationInSeconds: 200,
    album: {
      title: "Whenever You Need Somebody",
      year: 1987,
    },
  },
];

// VARIABLER
const songTitleElement = document.getElementById("song-title");
const songArtistElement = document.getElementById("song-artist");
const coverImageElement = document.getElementById(
  "cover-img"
) as HTMLImageElement;

const searchInput = document.querySelector("#search-input") as HTMLInputElement;

const songListContainer = document.querySelector("#song-list-container");
const playButton = document.querySelector("#play-btn") as HTMLButtonElement;
let status: PlayerStatus = "paused";

// LOGIK
playlist.forEach((song) => {
  const card = document.createElement("article");
  card.classList.add("song-card");

  const title = document.createElement("h3");
  title.textContent = song.title;

  const artist = document.createElement("span");
  artist.textContent = song.artist;

  card.append(title, artist);

  if (songListContainer) {
    card.addEventListener("click", () => {
      const currentActive = document.querySelector(".song-card.active");
      if (currentActive) {
        currentActive.classList.remove("active");
      }
      card.classList.add("active");
      playSong(song);
    });
    songListContainer.append(card);
  }
});

if (playButton) {
  playButton.addEventListener("click", () => {
    const iconElement = playButton.querySelector("span");

    if (status === "paused") {
      status = "playing";

      if (iconElement) {
        iconElement.textContent = "pause";
      }
    } else {
      status = "paused";
    }
    if (iconElement) {
      iconElement.textContent = "play_arrow";
    }
  });
}

if (searchInput) {
  searchInput.addEventListener("input", (e) => {
    const target = e.target as HTMLInputElement;
    const searchTerm = target.value.toLowerCase();

    const allCard = document.querySelectorAll(".song-card");

    allCard.forEach((card) => {
      const title = card.querySelector("h3")?.textContent?.toLowerCase();

      if (title?.includes(searchTerm)) {
        card.classList.remove("hidden");
      } else {
        card.classList.add("hidden");
      }
    });
  });
}

// FUNKTIONER
function playSong(song: Song) {
  if (songTitleElement) {
    songTitleElement.textContent = song.title;
  }

  if (songArtistElement) {
    songArtistElement.textContent = song.artist;
  }
}
```
