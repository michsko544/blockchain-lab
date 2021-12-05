# zadanie-1

Na początek zainstaluj potrzebne pakiety:
`npm install`

Aby odpalić skrypt użyj polecenia:
`npm start`

Powinieneś zobaczyć w konsoli 3 bloki w blockchainie.

Przyjrzyj się klasom i metodom dostępnym w pliku main.js

- W jakiej metodzie jest tworzony pierwszy blok łańcucha blockchain?
- Jaka funkcja hashująca jest używana do reprezentacji bloku?

Teraz sprawdzimy poprawności łańcucha przy użyciu metody `isChainValid`.
Metoda sprawdzająca poprawność łańcucha patrzy czy hash wyliczony z danych z bloku zgadza się z hashem podanym w bloku oraz czy poprzedni blok jest poprzednim blokiem.

Zakomentuj linijkę wyświetlającą w konsoli cały łańcuch.
Dodaj na dole pliku komendę wyświetlającą poprawność łańcucha:

```js
console.log(
  `Czy blockchain jest poprawny? ${myBlockchain.isChainValid() ? "Tak" : "Nie"}`
);
```

Następnie nadpisz wartość jednego z bloków:
`myBlockchain.chain[1].data = { amount: 1000 };`

i ponownie sprawdź poprawność łańcucha.

Pokazuje to że nie można tak łatwo zmienić wartości bloku żeby np. stać się bogatym.

Ok, ale ktoś może pomyśleć, że nadpiszę sobie wartość, jeszcze raz przelicze hash i powinno działać, sprawdźmy:
`myBlockchain.chain[1].hash = myBlockchain.chain[1].calculateHash();`

Jak widać wciąż poprawność jest zła. To dlatego, że relacja między blokami została zepsuta. Blockchain jest stworzony, aby dodawać do niego bloki, a nie zmieniać jego bloki czy je usuwać.

W sprawozdaniu umieścić screenshot z konsoli po nadpisaniu wartości bloku, ponownym wyliczeniu hasha i ponownym sprawdzeniu poprawności łańcucha.

Aby przejść do następnego zadania zmień gałąź komendą:
`git checkout zadanie-2`
