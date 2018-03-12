---
title: "Debugowanie Python kodu Linux komputerów zdalnych przy użyciu programu Visual Studio | Dokumentacja firmy Microsoft"
description: "Jak używać programu Visual Studio do debugowania kodu Python działającymi na komputerach zdalnych systemu Linux, łącznie z czynności konfiguracyjne niezbędne, zabezpieczeń i rozwiązywania problemów."
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 895abe0f9ce632f5c67c487726d0422607f8d427
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="remotely-debugging-python-code-on-linux"></a>Zdalne debugowanie kodu języka Python w systemie Linux

Program Visual Studio można uruchomić i debugowania aplikacji Python lokalnie i zdalnie na komputerze z systemem Windows (zobacz [zdalnego debugowania](../debugger/remote-debugging.md)). Można również debugowania zdalnego na różnych systemów operacyjnych, urządzenia lub Python wykonania innych niż z użyciem języka CPython [ptvsd biblioteki](https://pypi.python.org/pypi/ptvsd).

Używając ptvsd kodu Python debugowany obsługuje serwer debugowania, do którego można dołączyć program Visual Studio. Ta obsługa wymaga małych modyfikacji kodu zaimportować i włączyć serwer i może wymagać sieci lub zapory konfiguracji na komputerze zdalnym, aby zezwolić na połączenia TCP.

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | Aby obejrzeć wprowadzenie do debugowania zdalnego, zobacz [nowości: debugowanie zdalne i Platform](https://youtu.be/y1Qq7BrV6Cc) (witrynie youtube.com, 6m22s), która ma zastosowanie do programu Visual Studio 2015 i 2017 r. |

## <a name="setting-up-a-linux-computer"></a>Konfigurowanie komputera z systemem Linux

Do wykonania tego instruktażu potrzebne są następujące elementy:

- Komputera zdalnego z systemem Python w systemie operacyjnym, takich jak Mac OS x lub Linux.
- Port 5678 (przychodzące) otwarty na zaporze tego komputera, co jest ustawieniem domyślnym dla zdalnego debugowania.

Można jednak łatwo tworzyć [maszyn wirtualnych systemu Linux na platformie Azure](/azure/virtual-machines/linux/creation-choices) i [dostępu za pomocą pulpitu zdalnego](/azure/virtual-machines/linux/use-remote-desktop) z systemu Windows. Ubuntu dla maszyny Wirtualnej jest wygodne, ponieważ Python jest instalowane domyślnie; w przeciwnym razie zapoznaj się z listą na [zainstalować interpreter języka Python wybranym](installing-python-interpreters.md) dla języka Python dodatkowe lokalizacje.

Aby uzyskać więcej informacji na temat tworzenia reguły zapory dla maszyny Wirtualnej platformy Azure, zobacz [Otwieranie portów dla maszyny Wirtualnej na platformie Azure przy użyciu portalu Azure](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="preparing-the-script-for-debugging"></a>Przygotowywanie do debugowania skryptu

1. Na komputerze zdalnym, Utwórz plik Python o nazwie `guessing-game.py` z następującym kodem:

    ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
        guess = int(input('Take a guess: '))
        guesses_made += 1
        if guess < number:
            print('Your guess is too low.')
        if guess > number:
            print('Your guess is too high.')
        if guess == number:
            break
    if guess == number:
        print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
        print('Nope. The number I was thinking of was {0}'.format(number))
    ```

1. Zainstaluj `ptvsd` pakietu do przy użyciu środowiska `pip3 install ptvsd`. (Uwaga: jest dobrym pomysłem jest rekord wersji ptvsd, która jest zainstalowana w razie potrzeby go do rozwiązywania problemów; [listę ptvsd](https://pypi.python.org/pypi/ptvsd) dostępne wersje przedstawiono również.)

1. Włącz debugowanie zdalne przez dodanie poniższy kod w punkcie najwcześniejszą możliwe `guessing-game.py`, przed innymi kodu. (Chociaż ścisłe wymaganie, jest niemożliwe do debugowania wszystkie wątki w tle zduplikowany przed `enable_attach` funkcja jest wywoływana.)

   ```python
   import ptvsd
   ptvsd.enable_attach('my_secret')
   ```

   Pierwszy argument przekazany do `enable_attach` (o nazwie "poufne") ogranicza dostęp do uruchamianie skryptu, a następnie wprowadź ten klucz tajny podczas podłączania zdalnego debugera. (Chociaż nie jest to zalecane, można zezwolić wszystkim na połączenie, użyj `enable_attach(secret=None)`.)

1. Zapisz plik i uruchomić `python3 guessing-game.py`. Wywołanie `enable_attach` działa w tle i czeka na połączenia przychodzące, ponieważ w przeciwnym razie interakcji z programem. W razie potrzeby `wait_for_attach` funkcja może zostać wywołana po `enable_attach` blokowanie program, dopóki nie dołącza debuger.

> [!Tip]
> Oprócz `enable_attach` i `wait_for_attach`, ptvsd udostępnia również funkcję Pomocnika `break_into_debugger`, który służy jako punkt przerwania programowe, jeśli debuger jest dołączony. Istnieje również `is_attached` funkcja, która zwraca `True` Jeśli Debuger jest dołączony (należy pamiętać, że nie istnieje potrzeba do sprawdzenia tego wyniku przed wywołaniem innych `ptvsd` funkcji).

## <a name="attaching-remotely-from-python-tools"></a>Dołączanie zdalnie z narzędziami języka Python

W tych kroków możemy ustawić proste punkt przerwania, aby zatrzymać proces zdalny.

1. Tworzenie kopii pliku zdalnego na komputerze lokalnym, a następnie otwórz go w programie Visual Studio. Nie ma znaczenia, gdzie znajduje się plik, ale jego nazwa powinna odpowiadać nazwie skryptu na komputerze zdalnym.

1. (Opcjonalnie) Aby IntelliSense dla ptvsd na komputerze lokalnym, należy zainstalować pakiet ptvsd w środowisku Python.

1. Wybierz **Debuguj > dołączyć do procesu**.

1. W **dołączyć do procesu** okno dialogowe zostanie wyświetlone, ustaw **typ połączenia** do **zdalnego języka Python (ptvsd)**. (W starszych wersjach programu Visual Studio o nazwie tych poleceń **transportu** i **zdalnego debugowania języka Python**.)

1. W **element docelowy połączenia** pola (**kwalifikator** w starszych wersjach), wprowadź `tcp://<secret>@<ip_address>:5678` gdzie `<secret>` jest ciąg przekazany `enable_attach` w kodzie języka Python `<ip_address>` jest (co może być jawnego adresu lub nazwy, takie jak myvm.cloudapp.net) komputerem zdalnym i `:5678` numer portu to zdalnego debugowania.

    > [!Warning]
    > Jeśli wprowadzasz połączenie za pośrednictwem publicznej sieci internet, należy używać `tcps` zamiast i wykonując instrukcje poniżej dla [połączenia debugera przy użyciu protokołu SSL do zabezpieczania](#securing-the-debugger-connection-with-ssl).

1. Naciśnij klawisz Enter, aby wypełnić listę procesów ptvsd dostępne na tym komputerze:

    ![Wprowadzanie element docelowy połączenia i wyświetlanie listy procesów](media/remote-debugging-qualifier.png)

    W przypadku uruchamiania innego programu na komputerze zdalnym po wypełnieniu tej listy, wybierz **Odśwież** przycisku.

1. Wybierz proces do debugowania, a następnie **Attach**, lub kliknij dwukrotnie procesu.

1. Visual Studio następnie przełącza na tryb debugowania, gdy skrypt nadal działa na komputerze zdalnym, podając wszystkie zwykle [debugowania](debugging-python-in-visual-studio.md) możliwości. Na przykład ustawić punkt przerwania na `if guess < number:` wiersza, a następnie przełączyć się z komputerem zdalnym i wprowadź inny wynik. Możesz to zrobić, Visual Studio na zatrzymane z komputera lokalnego na ten punkt przerwania, aby zobaczyć zmiennych lokalnych i tak dalej:

    ![Trafiony punkt przerwania](media/remote-debugging-breakpoint-hit.png)

1. Po zatrzymaniu debugowania, Visual Studio odłączenie od program, który jest nadal uruchomiona na komputerze zdalnym. ptvsd nadal nasłuchuje dołączanie debugera, więc można ponownie dołączyć do procesu w dowolnym momencie ponownie.

### <a name="connection-troubleshooting"></a>Rozwiązywanie problemów z połączenia

1. Upewnij się, że wybrano **zdalnego języka Python (ptvsd)** dla **typ połączenia** (**zdalnego debugowania języka Python** dla **transportu** z starsze wersje.)
1. Sprawdź, czy klucz tajny w **element docelowy połączenia** (lub **kwalifikator**) dokładnie odpowiada klucz tajny w kodzie zdalnego.
1. Sprawdź, czy adres IP w **element docelowy połączenia** (lub **kwalifikator**) jest zgodna z komputera zdalnego.
1. Sprawdź otwarciu zdalnego debugowania port na komputerze zdalnym i że zostały dołączone sufiks portów w celu połączenia, takich jak `:5678`.
    - Jeśli musisz użyć innego portu, możesz je określić w `enable_attach` wywołanie przy użyciu `address` argumentu, jak w `ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))`. W takim przypadku można otworzyć określonego portu w zaporze.
1. Sprawdź, czy wersja ptvsd zainstalowana na komputerze zdalnym zwrócony przez `pip3 list` jest zgodna z wersji narzędzi języka Python, używane w programie Visual Studio w poniższej tabeli. W razie potrzeby zaktualizuj ptvsd na komputerze zdalnym.

    | Wersja programu Visual Studio | Wersja narzędzia/ptvsd języka Python |
    | --- | --- |
    | 2017 15.3 | 3.2.0 |
    | 2017 15.2 | 3.1.0 |
    | 2017 15.0, 15.1 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |

## <a name="securing-the-debugger-connection-with-ssl"></a>Zabezpieczanie połączenia debugera przy użyciu protokołu SSL

Domyślnie połączenie z serwerem zdalnego debugowania ptvsd jest zabezpieczone tylko klucz tajny i wszystkie dane są przekazywane w postaci zwykłego tekstu. W przypadku bardziej bezpieczne połączenia ptvsd obsługuje SSL, który ustawia się w następujący sposób:

1. Na komputerze zdalnym generowanie oddzielnych certyfikatu z podpisem własnym i pliki klucza przy użyciu biblioteki openssl:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    Po wyświetleniu monitu użyj nazwa hosta lub adres IP (zależności używane do łączenia) dla **nazwa pospolita** po wyświetleniu monitu przez biblioteki openssl.

    (Zobacz [certyfikaty z podpisem własnym](http://docs.python.org/3/library/ssl.html#self-signed-certificates) w języku Python `ssl` docs modułu, aby uzyskać dodatkowe szczegóły. Należy pamiętać, że polecenia w tych dokumentów generuje tylko pojedynczy plik połączony.)

1. W kodzie, zmodyfikuj wywołanie `enable_attach` uwzględnienie `certfile` i `keyfile` przy użyciu nazwy plików jako wartości argumentów (te argumenty mają takie samo znaczenie jak w przypadku standardowego `ssl.wrap_socket` funkcja Python):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    Można wprowadzić zmiany w pliku kodu na komputerze lokalnym, ale ponieważ ten kod nie jest aktualnie ma uruchomiony, jest bezwzględnie konieczne.

1. Uruchom ponownie program Python na komputerze zdalnym, dzięki czemu jest gotowy do debugowania.

1. Zabezpieczenia kanału, dodając certyfikatu zaufanego głównego urzędu certyfikacji na komputerze z systemem Windows z programem Visual Studio:

    1. Skopiuj plik certyfikatu z komputera zdalnego do komputera lokalnego.
    1. Otwórz Panel sterowania i przejdź do **narzędzia administracyjne > Zarządzanie certyfikatami komputera**.
    1. W wyświetlonym oknie rozwiń **zaufane główne urzędy certyfikacji** po lewej stronie kliknij prawym przyciskiem myszy **certyfikaty**i wybierz **wszystkie zadania > Import...** .
    1. Przejdź do i wybierz `.cer` skopiować pliku z komputera zdalnego, kliknij przycisk za pomocą okien dialogowych, aby zakończyć importowanie.

1. Powtórz procesu dołączania w programie Visual Studio jak opisano wcześniej, za pomocą `tcps://` jako protokół **element docelowy połączenia** (lub **kwalifikator**).

    ![Wybieranie transportu debugowania zdalnego przy użyciu protokołu SSL](media/remote-debugging-qualifier-ssl.png)

### <a name="warnings"></a>Ostrzeżenia

Visual Studio monituje o potencjalnych problemach certyfikatu podczas nawiązywania połączenia za pośrednictwem protokołu SSL zgodnie z poniższym opisem. Możesz zignorować ostrzeżenia i kontynuować, ale mimo, że kanał jest nadal będą szyfrowane przed podsłuchiwaniem może być otwarty na ataki man-in--middle.

1. Jeśli zostanie wyświetlone ostrzeżenie "certyfikat zdalny nie jest zaufany", oznacza to, że nie zostały poprawnie dodane certyfikatów do zaufanego głównego urzędu certyfikacji. Te kroki i spróbuj ponownie.

    ![Ostrzeżenie zaufany certyfikat SSL](media/remote-debugging-ssl-warning.png)

1. Jeśli zostanie wyświetlone ostrzeżenie "nazwy certyfikatu zdalnego nie jest zgodna nazwa hosta", to nie używasz prawidłowego hosta lub adres IP **nazwa pospolita** podczas tworzenia certyfikatu.

    ![Ostrzeżenie hostname certyfikatu SSL](media/remote-debugging-ssl-warning2.png)

> [!Warning]
> Obecnie 2017 usługi Visual Studio zawiesza się podczas możesz zignorować ostrzeżenia. Należy rozwiązać wszystkie problemy przed podjęciem próby połączenia.
