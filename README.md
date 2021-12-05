# zadanie-3

W tym zadaniu

- dodano klasę reprezentującą transakcję
- dodano otrzymywanie nagrody za wykopywanie
- dodano listę przechowującą oczekujące transakcje
- metodę wykopywania bloku dla oczekujących transakcji `minePendingTransactions`

Przejrzyj kod i zwróć uwagę na powyższe zmiany.

W Bitcoinie poprzez Proof-of-Work dodawany jest tylko jeden blok na 10 min. Wszystkie transakcje, które były zlecane są umieszczane w tablicy oczekujących transakcji, aby następnie były dodane jako jeden blok. System byłby bardzo niewydajny, gdyby górnik mógł obsłużyć tylko jedną transakcje zakładając, że transakcji jest więcej niż górników.

W prawdziwym blockchainie ilość transakcji jest zbyt duża żeby można było je wszystkie zawrzeć w bloku, więc osoba kopiąca - górnik wybiera, które transakcje będą dodane. Wybiera zwykle te, za które otrzyma największą nagrodę. 💸

W rzeczywistości nie ma w blockchainie czegoś co reprezentuje balans portfela. Jest jedynie lista wszystkich transakcji od początku, z której można wyliczyć sobie aktualny balans. W kodzie służy do tego metoda `getBalanceOfAddress`.

Utwórz dwie transakcje z adresu składającego się z 3 ostatnich cyfr numeru swojego albumu (Jeżeli dwie osoby w sekcji to po numerze na transakcje). Jako adres odbiorcy podaj kod pocztowym uczelni (44-100). Podaj dowolną ilość jaką chcesz przekazać uczelni:

```js
myBlockchain.addTransaction(new Transaction("XXX", "44-100", 1000));
myBlockchain.addTransaction(new Transaction("YYY", "44-100", 2000));
```

Następnie uruchom górnika, który obsłuży transakcje i wykopie blok. Jako adres górnika wpisz 'adres-gornika' :

```js
console.log("Uruchomienie górnika");
myBlockchain.minePendingTransactions("adres-gornika");
```

Teraz sprawdź bilans wszystkich użytych adresów:

```js
console.log(
  "Bilans konta gornika: " + myBlockchain.getBalaceOfAddress("adres-gornika")
);
console.log("Bilans konta XXX: " + myBlockchain.getBalaceOfAddress("XXX"));
console.log("Bilans konta YYY: " + myBlockchain.getBalaceOfAddress("YYY"));
console.log(
  "Bilans konta uczelni: " + myBlockchain.getBalaceOfAddress("44-100")
);
```

Uruchom skrypt `npm start`.

- Ile wynosi nagroda za wykopanie bloku?
- Jaki jest bilans górnika?

Ponownie uruchom górnika i sprawdź jeszcze raz jego bilans:

```js
console.log("Uruchomienie górnika ponownie");
myBlockchain.minePendingTransactions("adres-gornika");
console.log(
  "Bilans konta gornika: " + myBlockchain.getBalaceOfAddress("adres-gornika")
);
```

Uruchom ponownie skrypt i umieść w sprawozdaniu screenshot z konsoli.

- Czy bilans górnika się zmienił?
- Postaraj się wyjaśnić, dlaczego górnik dostał nagrodę z opóźnieniem - sprawdź zawartość tablicy `pendingTransactions`.
