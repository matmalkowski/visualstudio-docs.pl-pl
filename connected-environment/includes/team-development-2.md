2. Naciśnij klawisz F5 (lub typu `vsce up` okno terminalu) do uruchamiania usługi. W ten sposób automatycznie uruchomi go w naszym nowo wybrane miejsce `scott`. 
1. Firma Microsoft można potwierdzić, uruchamiając `vsce list` ponownie. Po pierwsze można zauważyć wystąpienia `mywebapi` działa teraz w `scott` miejsca (w wersji `mainline` jest nadal uruchomiony, ale nie ma na liście). Po drugie, adres URL z punktem dostępu `webfrontend` jest prefiksem tekst "scott —". Ten adres URL jest unikatowy dla `scott` miejsce i oznacza, że żądania wysyłane na "scott URL" podejmie próbę pierwszy trasy w usługach `scott` miejsce i powróci do usług w `mainline` miejsca.

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------
mywebapi     scott     mywebapi-0.1.0     80/TCP  15s ago     http://localhost:61466
webfrontend  mainline  webfrontend-0.1.0  80/TCP  5h ago      https://scott-webfrontend-contosodev.vsce.io
```

![](../media/space-routing.png)

Tej wbudowane możliwości środowiska połączony umożliwia przetestowanie kodu end-to-end w udostępnionym evironment bez konieczności wszystkich deweloperów ponownie utworzyć pełnego stosu usług w ich miejscu. Należy pamiętać, że marszruty wymaga nagłówki propagacji przekazywanych w kodzie aplikacji, zgodnie z opisami w poprzednim kroku w tym przewodniku.

## <a name="test-code-in-a-space"></a>Kod testu w miejscu
Aby przetestować naszej nowej wersji `mywebapi` w połączeniu z `webfrontend`, Otwórz w przeglądarce adres URL punktu dostępu publicznego webfrontend i przejdź do strony informacje. Wyświetlane nowe wiadomości powinna zostać wyświetlona.

Teraz Usuń "scott" części adresu URL i odświeżyć przeglądarkę. Powinny pojawić się stare zachowanie (eksponowane przez `mywebapi` wersji działającej `mainline`).