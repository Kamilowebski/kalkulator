# Kalkulator sieciowy

Kalkulator IPv4 w jednym pliku statycznym (`index.html`, Tailwind przez CDN), działa na GitHub Pages. Nie używa bazy ani logowania, wszystko liczy się w przeglądarce. W `localStorage` zapamiętywany jest tylko ostatnio wpisany adres.

Adres: https://kamilowebski.github.io/kalkulator/

## Funkcje

- wejście: `a.b.c.d/nn`, `a.b.c.d nn` albo `a.b.c.d maska` (bez prefiksu przyjmowane jest /32)
- wynik: adres, prefiks, maska, maska odwrotna (wildcard), adres sieci, broadcast, pierwszy i ostatni host, liczba hostów i adresów, klasa, typ adresu (prywatny RFC 1918, loopback, link-local, CGNAT, multicast, publiczny), przycisk kopiowania przy każdej wartości
- zapis binarny adresu, maski i sieci z wyróżnieniem bitów sieci i hosta
- podział na podsieci wybranym prefiksem lub według potrzebnej liczby hostów (tabela do 256 wierszy)
- sprawdzenie, czy adres należy do sieci
- ściągawka prefiksów /8–/32
- poprawna obsługa /31 (RFC 3021, 2 hosty) i /32 (1 host)

## Pliki

| Plik | Opis |
| --- | --- |
| `index.html` | cała aplikacja (HTML, Tailwind przez CDN, JS) |
| `manifest.webmanifest` | manifest PWA (nazwa, kolory, ikony) |
| `icons/` | favicon, ikona Apple Touch, ikony 192/512 i maskable |

## Uruchomienie

1. Wrzuć zawartość repozytorium na GitHub Pages (gałąź `main`, katalog główny) albo otwórz `index.html` lokalnie.
2. Dopisz stronę do listy `APPS` w `hub/apps.js` (id `kalkulator`, ścieżka `kalkulator/`).

Wymagany jest internet: Tailwind (CDN 3.4.17 z wtyczką forms, `colors.page = #f4f7f9`) oraz `kamilowebski.github.io/hub/apps.js`.

## Wspólny wygląd (Rejestr, Todo, Diary i nowe strony)

- tylko jasny motyw, tło `bg-page` (`#f4f7f9`), jeden akcent `blue-600`
- kontener `max-w-7xl mx-auto px-4 py-8 space-y-6`, nagłówek z tytułem po lewej i akcjami po prawej
- te same przyciski: główny (Dodaj, Zapisz), drugorzędny (Wyloguj, Anuluj), niebezpieczny (Usuń), ikony jako inline SVG
- logowanie jako karta `max-w-md` na stronie, okna `max-w-[560px]`, potwierdzenie `max-w-[400px]`
- przycisk huba (kwadraciki) w prawym górnym rogu, ładowany z `hub/apps.js` do `<div id="hub-apps">`

## Uwagi

- Kalkulator obsługuje tylko IPv4.
- Przy „ile hostów ma mieć podsieć" liczone jest klasycznie (bez adresu sieci i broadcastu), więc 2 hosty to /30.
