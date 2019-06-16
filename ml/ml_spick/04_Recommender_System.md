# Recommender System

## Scoring and Ranking Recommenders

- Popular way to counteract the new user cold start problem
- Make good baseline recommenders
- Stays stable
- Generates non-personalized recommendations

## Content-Based Recommendations

- Manuelle oder automatische Auswertung der Katalogdaten
- So viele Benutzerpräferenzen wie möglich sammeln
- Berechne Vorhersagen für Elemente, die mit ? gekennzeichnet sind, basierend auf der Artikelähnlichkeit
- Empfehlen von Artikeln mit hohen Vorhersagewert
- Only applicable to homogenous product catalogs
- Can also provide recommendation to anonymous users
- Can be set up even without ratings, usage or tracking data
- Are explicable to users

$$P_{uj} = \frac{\sum_{i \in {N_j}}sim(j, i) \times r_{ui}}{\sum_{i \in {N_j}}sim(j, i)}$$

$$P_{uj} = \text{How much does User u likes item j}$$

### Vorteile und Nachteile von Content-Based Recommendations

1. Benutzerunabhängigkeit und Transparenz
   - Profil eines Benutzers wird nur aus seinen eigenen Bewertungen erstellt
   - Empfehlungen können durch die Enthüllung relevanter Daten erklärt werden
2. Problem mit neuen Gegenständen (Cold Start Problem)
   - Kann neue Artikel ohne Bewertungen sofort empfehlen
3. Begrenzte Inhaltsanalyse
   - Spiegeln Attribute wirklich wieder, wie Benutzer entscheiden?
4. Überspezialisierung
   - Findet nie etwas Unerwartetes
   - Profile werden nur aus der Einkaufshistorie erstellt
5. Problem mit neuen Nutzern (Cold Start Problem)
   - Auch bei anonymen Benutzern
   - Hängt von Implementation ab, aber oft kein grosses Problem

## Collaborative Filtering

### User-to-User

- Empfehlungen sind aus Ansichten von ähnlichen Benutzern (Nachbarn)
- Hypothese: Benutzer die dasselbe in der Vergangenheit mochten, mögen auch das selbe in der Zukunft
- Produkte werden empfohlen, aufgrund von Produkten, welche die Nachbarn mögen, aber der aktuelle Benutzer noch nicht bewertet oder gekauft hat
- Keine Produktattribute nötig

 $$P_{uj} = \bar{r}_u + \frac{\sum_{i \in {N_u}}sim(u, i) \times (r_{ij} - \bar{r}_i)}{\sum_{i \in {N_u}}sim(u, i)}$$

$$P_{uj} = \text{How much does User u likes item j}$$
$$\bar{r}_u = \text{Average rating of user U}$$
$$r_{ij} = \text{Rating that neighbor i gave to item j}$$
$$\bar{r}_i = \text{Average Rating of neighbor i}$$

### Item-to-Item

- Da sich Benutzerprofile ständig ändern, funktioniert die Vorberechnung nicht
- Im Gegensatz dazu ist die Ähnlichkeit bei Item-Paaren stabil und kann vorberechnet werden

#### Berechnung

- Berechnungen sind identisch mit content-based recommendations
- Der einzige Unterschied besteht darin, wie die Ähnlichkeitmatrix berechnet wird:
  - Im Falle von Item-to-Item Collaborative Filtering bezieht sich diese Berechnung nur auf Benutzerbewertungen
  - Im Falle von content-based recommenders bezieht sich diese Berechnung auf Elementattribute

$$P_{uj} = \frac{\sum_{i \in {N_j}}sim(j, i) \times r_{ui}}{\sum_{i \in {N_j}}sim(j, i)}$$

$$P_{uj} = \text{How much does User u likes item j}$$


Berechnung sind identisch mit Content-based Rechnungen.

- Bei Item-to-Item Collaborative Fitlering werden die Userbewertungen mit einbezogen
- Bei content-based die Item Attribute

### Vorteile und Nachteile von Collaborative Filtering

1. Kategorieübergreifende Empfehlungen
   - Produkte aus verschiedenen Kategorien können empfohlen werden
2. Viele Personen müssen teilnehmen
   - In kleinen Matrizen werden keine Nachbarn gefunden
3. Problem mit neuen Benutzern (Coldstart problem)
   - System muss zunächst die Präferenz eines Benutzers aus seinen Bewertungen entnehmen
4. Problem mit neuen Gegenständen (Coldstart problem)
   - Viele Benutzer müssen neue Gegenstände bewerten, bevor sie empfohlen werden können
5. Grey Sheep Problem
   - Benutzer mit ungewöhnlichem Geschmeck erhalten keine genauen Empfehlungen

## Artikelähnlichkeit

- Je kleiner der Winkel zwischen den Produktvektoren, desto ähnlicher sind sie

$$ \text{similarity} = \frac{\sum_{i=1}^n A_i \times B_i}
{\sqrt{\sum_{i=1}^n (A_i)^2} \times \sqrt{\sum_{i=1}^n(B_i)^2}} $$

## Hybrid Systems

- Kombinieren von verschiedenen Algorithmen mit unterschiedlichen Vor- und Nachteilen, z.B. um das Cold Start Problem zu mildern, indem man content-based und collaborative recommenders kombiniert
- Gewichteter Ansatz
  - Bewerten von Gegenständen als gewichtete Summe der Punkte aus verschiedenen Maschienen
- Gemischter Ansatz
  - Ergebnisse verschiedener Methoden werdem dem Benutzer vorgestellt
- Kaskadenansatz
  - Empfehlungsmethode verfeiner das Ergebnis einer anderen Methode
- Wechselansatz
  - Online-shops können an verschiedenen Orten unterschiedliche Methoden anwenden

### Vorteile und Nachteile von Assoziationen

1. Einfach, schnell und günstig
   - Wenn Transaktionsdaten verwendet werden, ist keine Datenerfassung erforderlich
2. Assoziationen sind kontextbewust
   - Werden Produktpaare empfohlen, die gut zusammenpassen
3. Assoziationen können auf bestimmte Unternehmen zugeschnitten werden
   - Zeitlich begrenzte Assoziationen
   - "Kunden die gekauft haben" vs. "Kunden die angeschaut haben"
4. Nicht personalisierte Empfehlungen
   - Assoziationen betrachten Warenkörbe, nicht Einzelpersonen
   - Berücksichtigen keine persönlichen Preferenzen

## Implizite & Explizite Präferenzen

- Implizite: z.B. suchanfragen, seitenaufrufe, letztes login
- Explizite: z.B. bewerten, geburtstag, bildungslevel, sprache, like/dislike
