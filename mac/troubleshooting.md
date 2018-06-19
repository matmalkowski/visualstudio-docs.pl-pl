---
title: Visual Studio for Mac Rozwiązywanie problemów
description: Typowe problemy i rozwiązania dla programu Visual Studio dla użytkowników komputerów Mac.
ms.topic: troubleshooting
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: 135a71f18451eb209f9f351ae9224c1606bc50d6
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957541"
---
# <a name="troubleshooting"></a>Rozwiązywanie problemów

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Wyświetlanie dzienników w programie Visual Studio dla komputerów Mac

Dzienniki można znaleźć, przechodząc do **Pomoc > Otwórz katalog dziennika** element menu, jak przedstawiono poniżej:

![Otwórz element menu katalogu dziennika](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Wyświetlanie wyjątków

Jeśli został przechwycony wyjątek, zostanie wyświetlony bąbelków wyjątek. Aby wyświetlić bardziej szczegółowe informacje, wybierz **Wyświetl szczegóły** przycisk:

![Wyświetl szczegółowe informacje o wyjątku](media/troubleshooting-image2.png)

Spowoduje to wyświetlenie **Pokaż szczegóły** okna dialogowego i udostępnia dodatkowe informacje na temat wyjątek:

![Pokaż okno dialogowe szczegółów](media/troubleshooting-image3.png)

Ważne sekcje okno dialogowe, które są numerowane powyżej opisano szczegółowo poniżej:

1. Typ wyjątku, który zawiera pełną nazwę typu wyjątku, które są przestrzegane.
2. Komunikat wyjątku zawiera wartość właściwości komunikatu obiektu wyjątku.
3. Typ wyjątek wewnętrzny, który zawiera pełną nazwę typu wyjątku dla aktualnie wybranego wyjątku w widoku drzewa wyjątek wewnętrzny.
4. Komunikat wyjątku wewnętrznego, zawiera wartość właściwości komunikatu wyjątku wybranego w widoku drzewa wyjątek wewnętrzny.
5. Wyświetl ślad stosu. To może zostać zwinięty za pomocą strzałki ujawnienie i zawiera wpisy ramki stosu.
6. Przykład wpisy kodu innych użytkowników.
7. Przykład wpisów kodu użytkownika.
8. Właściwości widoku, który zawiera wszystkie właściwości i pola wyjątku. Może to zostać zwinięty za pomocą strzałki ujawnienie.
9. Widok drzewa wyjątek wewnętrzny. W tym widoku za pomocą klawiatury strzałki w górę lub w dół lub za pomocą myszy lub trackpad wybierz wyjątków wewnętrznych.
10. Domyślnie ta jest równa co **debugowania tylko kodu projektu** ustawiono opcję w ustawieniach debugera. Po zaznaczeniu tego pola spowoduje włączenie wszystkich kodu innych użytkowników zwinąć w jednym wierszu w ślad stosu.
11. Przycisk Kopiuj, aby skopiować `exception.ToString()` dane wyjściowe do Schowka.

Należy pamiętać, że niektóre z tych sekcji będą widoczne tylko, gdy wyjątek ma wyjątek wewnętrzny.