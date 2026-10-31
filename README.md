# WebFlyx

Mały zbiór danych o filmach zapisany w Markdown i CSV. Repozytorium zawiera listę tytułów, klasyki z reżyserem i rokiem premiery oraz cytaty pogrupowane według filmów.

To repozytorium danych i plików tekstowych — nie zawiera aplikacji streamingowej ani kodu serwera.

## Zawartość

| Plik | Zawartość |
| --- | --- |
| [`contents.md`](contents.md) | Krótki indeks kolekcji |
| [`titles.md`](titles.md) | Lista tytułów w Markdown |
| [`classics.csv`](classics.csv) | Kolumny `title`, `director`, `year` |
| [`quotes/dune.md`](quotes/dune.md) | Cytaty z filmu *Dune* |
| [`quotes/starwars.md`](quotes/starwars.md) | Cytaty z *Star Wars* |

## Jak korzystać

Pliki można czytać bezpośrednio na GitHubie lub w dowolnym edytorze tekstu. Nie trzeba instalować zależności, konfigurować zmiennych środowiskowych ani uruchamiać procesu budowania.

```sh
git clone https://github.com/dzwoniar/webflyx.git
cd webflyx
```

`classics.csv` można otworzyć w arkuszu kalkulacyjnym z separatorem przecinka. Po przecinkach występują spacje; przy programowym odczycie warto je pomijać.

Przykład w standardowej bibliotece Pythona 3, uruchamiany z katalogu repozytorium:

```python
import csv
from pathlib import Path

with Path("classics.csv").open(encoding="utf-8", newline="") as file:
    films = list(csv.DictReader(file, skipinitialspace=True))

for film in films:
    print(f"{film['title']} ({film['year']}) — {film['director']}")
```

## Edycja i zakres

Nowy film dopisz do odpowiedniej listy, zachowując nagłówek CSV i trzy kolumny. Cytaty umieszczaj w katalogu `quotes/`, a przy dodawaniu nowych plików aktualizuj `contents.md`.

Repozytorium nie zawiera wyszukiwarki, API, bazy danych ani testów automatycznych. Listy są niezależnymi plikami i nie synchronizują się automatycznie.
