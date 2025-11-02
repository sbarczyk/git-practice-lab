
# RAPORT GIT — Laboratorium AGH

Raport z zajęć laboratoryjnych z systemu kontroli wersji **Git**  
Wydział Informatyki, Akademia Górniczo-Hutnicza w Krakowie  

Zadania pochodzą z platformy: [https://gitexercises.fracz.com](https://gitexercises.fracz.com)

---

RAPORT Z WYDARZENIA:
„Dziady są Git”

E-mail do weryfikacji wykonanych zadań:
Zadania wykonałem już miesiąc temu (po pierwszych labolatoriach programowania obiektowego).

## Zadanie 1: Master
```bash
git verify
```

## Zadanie 2: Commit one file
```bash
git add A.txt
```
```bash
git commit -m "Commit A.txt file"
```

## Zadanie 3: Commit one file of two currently staged
```bash
git reset A.txt
```
```bash
git commit -m "Commit B.txt file"
```

## Zadanie 4: Ignore unwanted files
echo *.exe > .gitignore
echo *.o >> .gitignore
echo *.jar >> .gitignore
echo libraries/ >> .gitignore
```bash
git add .gitignore
```
```bash
git commit -m "Ignore unwanted files"
```

W tym zadaniu echo jest używane do zapisywania wzorców plików, które mają być ignorowane przez system kontroli wersji Git.
W skrócie, komenda
echo tekst >> plik
umieszcza tekst w pliku.

## Zadanie 5: Chase branch that escaped
```bash
git merge escaped
```

## Zadanie 6: Resolve a merge conflict
```bash
git merge another-piece-of-work
```
Rozwiązujemy konflikt z pomocą wbudowanego edytora.
```bash
git add equation.txt
```
```bash
git commit --no-edit
```
Opcja –no-edit pozwala na dokonanie commitu bez zmieniania istniejącej wiadomości.

## Zadanie 7: Saving your work
```bash
git stash
```
### Komenda git stash pozwala tymczasowo zapisać zmiany w repozytorium Git bez konieczności tworzenia commitu (zapisuje zmiany lokalnie, które później możemy przywrócić z wykorzystaniem komendy git stash pop)
fix a bug in bug.txt file
```bash
git commit -am "Fix a bug"
```
```bash
git stash pop
```
echo "Finally, finished it!" >> bug.txt
```bash
git commit -am "Finish my work"
```

## Zadanie 8: Change branch history
```bash
git rebase hot-bugfix
```
```bash
git rebase jest poleceniem Gita, które pozwala zmienić bazę (czyli punkt startowy) jednej lub więcej gałęzi lub commitów. Jest to przydatne do uporządkowania historii commitów, integracji zmian z innej gałęzi lub przenoszenia zmian na inny punkt w historii projektu.
```
W naszym przypadku git rebase przepisuje historię naszej gałęzi, tak jakby nasze commity były utworzone bezpośrednio na końcu głównej gałęzi.

## Zadanie 9: Remove ignored file
```bash
git rm ignored.txt
```
### Komenda ta usuwa plik ignored.txt z repozytorium
```bash
git commit -am "Remove the file that should have been ignored"
```
Opcja -a pozwala na automatyczne dodanie zmian (nie trzeba wtedy używać git add .)

## Zadanie 10: Change a letter case in the filename of an already tracked file
```bash
git mv File.txt file.txt
```
```bash
git commit -am "Change name of file.txt"
```

## Zadanie 11: Fix typographic mistake in the last commit
Popraw literówkę w pliku:
Otwórz file.txt w edytorze tekstu i zamień “wordl” na “world”.
Zamień poprzedni commit:
Użycie komendy
```bash
git commit – a --amend,
```
aby zmodyfikować ostatni commit, uwzględniając zarówno poprawiony plik, jak i nową wiadomość commita.

## Zadanie 12: Forge the commit's date
```bash
git commit --amend --no-edit --date="1987-08-03"
```
1. --amend: Modyfikuje ostatni commit, aby wprowadzić w nim zmiany.
2. --no-edit: Nie otwiera edytora wiadomości commita. Wykorzystuje wiadomość z poprzedniego commita, pozostawiając ją bez zmian.
3. --date="1987-08-03": Ustawia datę commita na podaną wartość, w tym przypadku na “3 sierpnia 1987”.

## Zadanie 13: Fix typographic mistake in old commit
```bash
git rebase -i HEAD~2
```
W edytorze: Zaznaczenie commita do edycji
W edytorze przy commitcie, który chcemy edytować, zamieniamy pick na edit.
Dzięki temu git wie, że chcemy zatrzymać rebase na tym commitcie, aby go edytować.
Poprawienie literówki w pliku
Teraz, gdy zatrzymano rebase na wybranym commitcie, można poprawić literówkę bezpośrednio w pliku (file.txt).
```bash
git add file.txt
```
```bash
git rebase –continue
```
Naprawiamy literówkę w wiadomości commita.

## Zadanie 14: Find a commit that has been lost
```bash
git reflog
```
To polecenie wyświetla historię wszystkich operacji wykonanych na bieżącej gałęzi, takich jak commity, resety, merge’y, cherry-picki, rebase’y i inne.
Każdy wpis w reflogu ma unikalny numer identyfikacyjny, np. HEAD@{1}, HEAD@{2}, itp., które oznaczają kolejne zmiany w repozytorium, gdzie HEAD@{0} to najnowsza zmiana.
```bash
git reset --hard HEAD@{1}
```
To polecenie usuwa wszystkie zmiany wprowadzone po HEAD@{1} (łącznie z niezatwierdzonymi zmianami) i przywraca repozytorium do stanu sprzed ostatniej operacji.

## Zadanie 15: Split the last commit
```bash
git reset HEAD~1
```
```bash
git reset HEAD~1 przesuwa wskaźnik HEAD o jeden commit wstecz, usuwając ostatni commit z historii, ale zostawiając zmiany z tego commita jako niezatwierdzone w staging area (czyli w obszarze indeksu). Dzięki temu zmiany są nadal widoczne w git status, ale nie są już częścią historii commitów.
```
```bash
git add first.txt
```
```bash
git commit -m "First.txt"
```
```bash
git add second.txt
```
```bash
git commit -m "Second.txt"
```

## Zadanie 16: Too many commits
```bash
git rebase -i HEAD^^
```
"squash" the second commit
Otworzy się edytor z listą commitów. Wybieramy opcję "squash" dla drugiego commita:
squash: Łączy zmiany z drugiego commita z pierwszym i umożliwia edytowanie wiadomości commita.

## Zadanie 17: Make the file executable by default
chmod +x script.sh
```bash
git add script.sh
```
```bash
git commit -m "Set script.sh as executable"
```

## Zadanie 18: Commit part of work
```bash
git add -p file.txt
```
### Komenda git add -p file.txt służy do interaktywnego dodawania fragmentów (tzw. “hunks”) zmian w pliku do indeksu Git. Jest to przydatne, gdy chcemy dodać tylko wybrane części zmian w pliku zamiast dodawać wszystkie zmiany na raz.
Wybieramy co chcemy umieścić w pierwszym commicie:
```bash
git commit -m "First part of changes"
```
```bash
git commit -am "The rest of the changed"
```

## Zadanie 19: Pick your features
```bash
git cherry-pick feature-a
```
```bash
git cherry-pick feature-b
```
```bash
git cherry-pick feature-c
```
Rozwiązanie konfliktu z pomocą wbudowanego edytora.
```bash
git add -A
```
```bash
git cherry-pick –continue
```
W skrócie, ten proces przenosi konkretne commity (feature-a, feature-b, feature-c) na bieżącą gałąź. W przypadku konfliktów, musimy rozwiązać je ręcznie, dodać zmiany do indeksu, a następnie kontynuować cherry-pick (aby kontynuować proces cherry-pickowania i zakończyć aktualny commit, który wcześniej został zatrzymany z powodu konfliktów)

## Zadanie 20: Rebase complex
```bash
git rebase issue-555 --onto your-master
```
### Komenda ta oznacza prostymi słowami: Pobierz wszystkie commity, które nie znajdują się na gałęzi issue-555, i umieść je na your-master.”

## Zadanie 21: Change order of commits
```bash
git rebase -i HEAD~2
```
Przenieś drugi commit wyżej
Oznacza to, że otworzy się edytor, w którym zobaczymy listę dwóch ostatnich commitów (najnowszy na dole).
Aby „przenieść drugi commit w górę,” czyli sprawić, by commit starszy pojawił się po nowszym, musimy po prostu zmienić kolejność tych dwóch linii w edytorze.

## Zadanie 22: Find commits that introduced swearwords
```bash
git log -S shit
```
Ta komenda przeszukuje historię commitów i pokazuje ID commitów, które zawierają określone słowo (w tym przypadku „shit”). Flaga -S wyszukuje zmiany, które wprowadziły to słowo.
```bash
git rebase -i <commit ID>^
```
Używamy ID znalezionego commita i uruchamiamy interaktywny rebase na commitach pochodzących przed nim. Dodanie ^ oznacza, że rebase będzie dotyczyć commitów od razu przed podanym ID.
Teraz usuwamy niechciane słowa:
W interaktywnym rebase, kiedy edytor się otworzy, znajdź linijkę z komendą edit dla commita, który chcesz zmodyfikować, i usuń niechciane słowo w odpowiednich plikach.
```bash
git add .
```
```bash
git rebase –continue
```
Po zapisaniu zmian i dodaniu ich do commita, kontynuuj rebase. Git zakończy rebase, jeśli nie ma innych commitów do zmodyfikowania.

## Zadanie 23: Find commit that has introduced bug
```bash
git bisect start
```
Poprzez tę komendę rozpoczynamy proces poszukiwania błędu.
```bash
git bisect bad HEAD
```
Tutaj oznaczamy HEAD (czyli ostatni commit) jako „zły” commit, w którym występuje błąd.
```bash
git bisect good 1.0
```
Tutaj wskazujemy commit oznaczony 1.0 jako „dobry” commit, czyli taki, w którym błąd jeszcze nie występował. git bisect będzie teraz przeszukiwać commit po commitcie między „dobrym” a „złym”, aby znaleźć dokładny moment, w którym błąd został wprowadzony.
```bash
git bisect run sh -c "openssl enc -base64 -A -d < home-screen-text.txt | grep -v jackass"
```
Ta komenda automatycznie uruchamia git bisect run z podanym poleceniem, które będzie testem sprawdzającym utworzonym z pomocą wskazówki zawartej w zadaniu.
Dekoduje plik home-screen-text.txt z kodowania base64 za pomocą openssl.
Wyszukuje w wyniku słowo „jackass”.
Jeśli wynik zawiera to słowo, oznacza to, że commit jest „zły”; jeśli nie, commit jest „dobry”.





















---

## Podsumowanie / Czego się nauczyłem

Podczas realizacji zadań nauczyłem się praktycznego korzystania z **Gita** – od podstawowych commitów, pracy z gałęziami i łączeniem zmian, po bardziej zaawansowane operacje takie jak **rebase**, **cherry-pick**, czy **bisect**.  
Dzięki tym ćwiczeniom lepiej rozumiem proces kontroli wersji i potrafię efektywnie pracować z repozytoriami w środowisku zespołowym.
