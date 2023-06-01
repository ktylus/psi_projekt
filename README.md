# PSI - projekt zaliczeniowy

W projekcie wykorzystuję zbiór danych: https://www.kaggle.com/datasets/yasserh/wine-quality-dataset

Projekt polega na predykcji oceny wina na podstawie jego parametrów. Ocena może wynosić od 0 do 10.
Jest to interesujący problem, ponieważ można go potraktować jako klasyfikację, nie wykorzystując w ten sposób porządku na ocenach (np. 7 > 6, ale jednocześnie 8 > 7 > 6 itd.), a także
można ten porządek wykorzystać, wtedy wydaje się, że można nazwać to regresją, choć na liczbach naturalnych.

Zrobiłem to w pierwszy sposób, ponieważ nie wiedziałem, jak zrealizować to w ten drugi sposób. Próbowałem przez chwilę czytać o tym w internecie
i odniosłem wrażenie, że rozwiązanie problemu regresji na takich danych nie jest łatwe do zaimplementowania.

Wydaje mi się, że te dwa podejścia nie powinny się różnić zbyt bardzo w swojej skuteczności, ponieważ porządek ocen jest już zawarty w danych - wina bardzo podobne nie będą posiadać
bardzo różnych ocen.

## Eksploracja danych

W pliku data_exploration.ipynb wykonałem krótką eksplorację danych, aby dowiedzieć się więcej o wartościach kolumn oraz o targecie.
W przypadku tego drugiego udało się dokonać istotnych obserwacji.

## Przygotowanie danych do modelowania

W zbiorze danych nie było żadnych wartości brakujących. Dodałem je sam poprzez wylosowanie w każdej kolumnie (poza targetem) 5% wartości, które zamieniłem na NaN.
Poza skalowaniem i imputacją w pipeline nie było konieczności zastosowania innych kroków przetwarzania danych.

## Modelowanie

Nauczyłem 5 modeli płytkich oraz 2 rodzaje sieci neuronowych (fully connected oraz konwolucyjna). W przypadku modeli płytkich wykorzystałem do tego grid search, by znaleźć jak najlepsze parametry.
W przypadku uczenia sieci nie zastosowałem cross-validation, zamiast tego odłożyłem 10% danych jako zbiór walidacyjny.
Oprócz tego odłożyłem 10% danych jako zbiór testowy.
Ostatecznie cross-validation odbywało się na 90% danych, ponieważ włączony został do nich zbiór walidacyjny, który wykorzystałem tylko podczas trenowania sieci.

## Wyniki

Najlepszym modelem okazał się Random Forest, który w 74% przypadkach poprawnie przewidział ocenę win w zbiorze testowym.
Na końcu notebooku znajdują się wizualizacje ilustrujące wynik.
