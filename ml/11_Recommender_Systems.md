# Recommender Systems

## Definition

- Ein Empfehlungssystem ist jedes System, das individualisierte Empfehlungen als Ergebnis erzeugt oder den Benutzer auf personalisierte Weise zu interessanten oder nützlichen Objekten in einem grossen Bereich möglicher Optionen führt
- Ein Empfehlungssystem ist eine Softwareanwendung, die in der Lage ist, ihren Benutzern interessante Dinge vorzuschlagen, nachdem sie ihre Präferenzen im Laufe der Zeit gelernt haben

## Zweck

- Kundenperspektive: Unterstützung der Benutzer bei der Bewältigung des Problems der Informationsüberlastung
- Geschäftsperspektive: effektive Möglichkeit, mehr Umsatz zu erzielen oder das Engagement der von ihnen angebotenen Dienstleistungen zu erhöhen

## Assoziationen

### Berechnung von Assoziationen

- Prozent von $X$ Käufern welche ausserdem $Y$ gekauft haben

$$ \frac{X \text{ and } Y}{X} : \frac{\neg X \text{ and } Y}{\neg X} $$

- Kompensiert die Gesamtpopularität von Y

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

## Content-Based Recommendations

- Manuelle oder automatische Auswertung der Katalogdaten
- So viele Benutzerpräferenzen wie möglich sammeln
- Berechne Vorhersagen für Elemente, die mit ? gekennzeichnet sind, basierend auf der Artikelähnlichkeit
- Empfehlen von Artikeln mit hohen Vorhersagewert

$$ \includegraphics[width=0.7\columnwidth]{images/content_based_recommendations.png} $$

### Artikelähnlichkeit

- Je kleiner der Winkel zwischen den Produktvektoren, desto ähnlicher sind sie

$$ \includegraphics[width=0.7\columnwidth]{images/item_similarity.png} $$

$$ \text{similarity} = \frac{\sum_{i=1}^n A_i \times B_i}
{\sqrt{\sum_{i=1}^n (A_i)^2} \times \sqrt{\sum_{i=1}^n(B_i)^2}} $$

### Ähnlichkeitsmatrix

$$ \includegraphics[width=0.7\columnwidth]{images/similarity_matrix.png} $$

### Beispiel

$$ \includegraphics[width=0.7\columnwidth]{images/content_based_recommendation_example.png} $$

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

$$ \includegraphics[width=0.7\columnwidth]{images/user_to_user_collaborative_filtering.png} $$

#### Beispiel

$$ \includegraphics[width=0.7\columnwidth]{images/user_to_user_collaborative_filtering_example.png} $$

### Item-to-Item

- Da sich Benutzerprofile ständig ändern, funktioniert die Vorberechnung nicht
- Im Gegensatz dazu ist die Ähnlichkeit bei Item-Paaren stabil und kann vorberechnet werden

$$ \includegraphics[width=0.4\columnwidth]{images/item_to_item_collaborative_filtering_formula.png} $$

#### Berechnung

- Berechnungen sind identisch mit content-based recommendations
- Der einzige Unterschied besteht darin, wie die Ähnlichkeitmatrix berechnet wird:
  - Im Falle von Item-to-Item Collaborative Filtering bezieht sich diese Berechnung nur auf Benutzerbewertungen
  - Im Falle von content-based recommenders bezieht sich diese Berechnung auf Elementattribute

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

## Hybride Recommender Systeme

- Kombinieren von verschiedenen Algorithmen mit unterschiedlichen Vor- und Nachteilen, z.B. um das Cold Start Problem zu mildern, indem man content-based und collaborative recommenders kombiniert
- Gewichteter Ansatz
  - Bewerten von Gegenständen als gewichtete Summe der Punkte aus verschiedenen Maschienen
- Gemischter Ansatz
  - Ergebnisse verschiedener Methoden werdem dem Benutzer vorgestellt
- Kaskadenansatz
  - Empfehlungsmethode verfeiner das Ergebnis einer anderen Methode
- Wechselansatz
  - Online-shops können an verschiedenen Orten unterschiedliche Methoden anwenden

## Bewerten von Recommender Systemen

- Bewertung eines Empfehlungssystems ist nicht einfach, ein Train/Test/Validation Split funktioniert nicht
- Teilen der Sets von jeder einzelnen Person zum testen, gesamte Einkaufshistorie wird gebraucht (alle Einkäufe jeder Person wird gesplittet)
- Verwenden von P@k als Metrix für Empfehlungssysteme, d.h. unter den k ausgewählten Artikel, wie viele relevant sind (gekauft, bewertet, angesehen)
- minP@k verwenden, wenn viele Benutzer weniger als k relevante Produkte haben
- Wenn ein Produkt nicht von einem bestimmten Benutzer bewertet wurde, bedeutet das wirklich, dass das Produkt irrelevant ist - vielleicht ist der Benutzer einfach nicht auf dieses Produkt gestoßen.
einen Katalog mit Tausenden von Artikeln
- Recommenders haben in der Regel sehr niedrige P@k-Werte
