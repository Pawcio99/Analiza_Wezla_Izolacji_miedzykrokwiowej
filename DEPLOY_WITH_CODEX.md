# Publikacja przez Codex — bez naruszania istniejącej strony

## Cel
Opublikować katalog `gable-wall-multiphysics-publication-v2` jako osobną publikację w istniejącym repozytorium GitHub Pages `pawcio99.github.io`, preferowany adres:

`https://pawcio99.github.io/research/gable-wall-multiphysics/`

Nie zmieniaj strony głównej ani istniejących podstron poza ewentualnym dodaniem pojedynczego linku do publikacji, jeśli użytkownik później o to poprosi.

## Prompt do wklejenia do Codex

Pracujesz w moim lokalnym repozytorium GitHub Pages. Najpierw wykonaj audyt struktury repozytorium i ustal, z jakiej gałęzi oraz katalogu publikowane jest GitHub Pages. Nie zmieniaj istniejącego frontendu strony głównej.

Mam gotową statyczną publikację w katalogu:
`/ŚCIEŻKA/DO/gable-wall-multiphysics-publication-v2/`

Chcę ją opublikować pod:
`/research/gable-wall-multiphysics/`

Wykonaj kolejno:
1. `git status`, identyfikacja bieżącej gałęzi i `git remote -v`.
2. Sprawdź strukturę repozytorium oraz konfigurację GitHub Pages/Jekyll/Actions, jeśli istnieje.
3. Utwórz osobny katalog publikacji `research/gable-wall-multiphysics/` w katalogu faktycznie publikowanym przez Pages.
4. Skopiuj do niego wyłącznie pliki publikacji: `index.html`, `styles.css`, `script.js`, `LICENSE.md`, `CITATION.cff`, `README.md`, `.nojekyll`.
5. Nie modyfikuj treści naukowej, nazwiska autora, licencji ani bibliografii bez mojego polecenia.
6. Zachowaj wszystkie odnośniki względne tak, aby podstrona działała pod wskazanym URL-em.
7. Sprawdź statycznie HTML/CSS/JS: brak brakujących lokalnych zasobów, poprawne ścieżki, poprawne odwołania do `LICENSE.md`, brak błędnych kotwic spisu treści.
8. Jeśli w systemie jest dostępna przeglądarka/headless Chromium, uruchom lokalny serwer HTTP i wykonaj kontrolę desktop 1440 px oraz mobile 390 px. Napraw wyłącznie błędy frontendowe, bez redagowania treści naukowej.
9. Pokaż mi `git diff --stat` i skrócone `git diff` przed commitem. Jeśli nie ma regresji, wykonaj commit:
   `publish gable-wall multiphysics critical review`
10. Wypchnij commit do gałęzi publikowanej przez GitHub Pages.
11. Na końcu podaj dokładny przewidywany URL publikacji i listę zmienionych plików.

Zasada bezpieczeństwa: nie kasuj, nie przenoś i nie nadpisuj istniejących plików strony głównej. Jeżeli struktura repozytorium jest inna niż zakładana, dostosuj ścieżkę docelową do konfiguracji Pages zamiast przebudowywać repozytorium.

## Minimalna sekwencja terminalowa, jeśli repo publikuje bezpośrednio z root `main`

```bash
cd ~/SCIEZKA/DO/pawcio99.github.io

git status
git branch --show-current
git remote -v

mkdir -p research/gable-wall-multiphysics
cp -a /SCIEZKA/DO/gable-wall-multiphysics-publication-v2/. \
  research/gable-wall-multiphysics/

# Plik wdrożeniowy nie musi być częścią publicznej strony.
rm -f research/gable-wall-multiphysics/DEPLOY_WITH_CODEX.md

git diff --check
git status --short
git diff --stat

python3 -m http.server 8080
# test w przeglądarce:
# http://127.0.0.1:8080/research/gable-wall-multiphysics/
```

Po kontroli:

```bash
git add research/gable-wall-multiphysics
git commit -m "publish gable-wall multiphysics critical review"
git push
```
