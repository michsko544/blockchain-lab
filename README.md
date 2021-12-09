# zadanie-2

W kodzie z poprzedniego ćwiczenia możemy dodawać bloki w szybki sposób. Wystarczy utworzyć blok, obliczyć jego hasz i dodać do łańcucha. Nowoczesne komputery potrafią takie rzeczy robić bardzo szybko, a przecież nie chcemy, aby ludzie tworzyli tysiące bloków na sekundę i mieli możliwość zaśmiecania blockchaina. Dodatkowo pojawia się problem bezpieczeństwa, bo ktoś może zmodyfikować sobie blok, a następnie wygenerować poprawne hasze bloków za zmodyfikowanym, tworząc poprawny łańcuch.

I tutaj pojawia się koncepcja Proof-of-Work (PoW). Polega to na wykorzystaniu dużej mocy obliczeniowej do utworzenia bloku. Ten proces również nazywa się kopaniem. Bitcoin np. wymaga, aby hasz zaczynał się od specyficznej ilości zer. Ponieważ nie można wpłynąć na wynik funkcji haszującej, dlatego trzeba spróbować dużą liczbę kombinacji, aby odnaleźć odpowiedni hasz.

**Ciekawostka** Twórca Bitcoina założył również, że komputery z czasem będą coraz szybsze, dlatego co średnio 4 lata trudność znalezienia odpowiedniego haszu jest utrudniana (jest to tzw 'halving').

W tym zadaniu skupimy się na mechanizmie Proof-of-Work. Chcemy, aby hasz na początku posiadał specyficzną ilość zer, ale patrząc na informacje zawarte w bloku, wynik funkcji haszującej będzie zawsze taki sam. Potrzebna jest jakaś wartość, która będzie się zmieniać co zapewni różne hasze za każdym razem. Blockchain posiada coś takiego jak wartość `nonce`, która może być np. ustawiona na wartość losową.

Przyjrzyj się nowej metodzie `mineBlock` oraz zmianie w metodach `calculateHash` i `addBlock`.

- jaką wartość przyjmuję `nonce` w naszym skrypcie po każdym wyliczeniu?
- na ile ustawiona jest wartość `difficulty`?

Na dole skryptu dodaj do blockchaina blok oraz zmierz czas obliczania jego haszu:

```js
console.time("Czas kopania");
console.log("Kopanie bloku 1...");
myBlockchain.addBlock(new Block(1, "05/12/2021", { amount: 100 }));
console.timeEnd("Czas kopania");
```

Pod spodem tak samo dodaj następny blok podając inne wartości.

W sprawozdaniu zamieść screenshot konsoli z czasami kopania obu bloków.

Następnie zmień wartość `difficulty` w klasie `Blockchain` na 6. Uruchom skrypt i poczekaj aż bloki zostaną wydobyte. W sprawozadniu umieść również screenshot z konsoli po zmianie `difficulty` i wydobyciu obu bloków.

Aby przejść do następnego zadania
wejdź w link [https://stackblitz.com/github/michsko544/blockchain-lab/tree/zadanie-3](https://stackblitz.com/github/michsko544/blockchain-lab/tree/zadanie-3)
lub zmień gałąź komendą:
`git checkout zadanie-3`
