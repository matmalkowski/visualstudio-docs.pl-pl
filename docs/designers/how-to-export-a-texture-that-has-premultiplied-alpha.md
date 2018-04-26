---
title: 'Porady: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e72a64559953e5e111d270f259ed66e10c97e54
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Porady: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa
Potok zawartości obrazu można wygenerować wstępnie przemnożone tekstury alfa z obrazu źródłowego. Mogą to być umożliwia łatwiejsze i bardziej niezawodna niż tekstury, które nie zawierają wstępnie przemnożone alfa.

 W tym dokumencie przedstawiono następujące działania:

-   Konfigurowanie obrazu źródłowego do przetworzenia przez potok zawartości obrazu.

-   Konfigurowanie potoku zawartości obrazu do generowania wstępnie przemnożone alfa.

## <a name="premultiplied-alpha"></a>Wstępnie przemnożone alfa
 Alpha wstępnie przemnożone oferuje kilka zalet w porównaniu z konwencjonalnych, wstępnie przemnożone alfa, ponieważ lepiej reprezentuje interakcji rzeczywistych światła materiałami fizycznych oddzielając udział koloru materiału teksela (kolor, który dodaje do sceny) z jego przejrzystości (ilość koloru źródłowego, umożliwiający za pośrednictwem). Zalety korzystania z wstępnie przemnożone alfa należą:

-   Przenikanie alfa wstępnie przemnożone jest operacją asocjacyjnej; przenikanie wielu tekstury półprzezroczyste wynikiem jest taki sam, niezależnie od tego, w kolejności, w którym są mieszane tekstury.

-   Z powodu asocjacyjnej charakter przenikanie alfa wstępnie przemnożone upraszcza renderowania wielu przebiegu przezroczystych obiektów.

-   Za pomocą wstępnie przemnożone alfa, zarówno czysty dodatku mieszania (przez ustawienie alfa od zera) i liniowo interpolowane mieszania można osiągnąć, jednocześnie. Na przykład w systemie cząstki cząstki additively mieszanych fire może stać się cząstka dymu półprzezroczyste mieszania przy użyciu interpolacji liniowej. Bez wstępnie przemnożone alfa trzeba narysować cząstki fire oddzielnie od dymu cząstek i modyfikowania stanu renderowania między wywołań rysowania.

-   Kompresuj tekstury, korzystających z wstępnie przemnożone alfa lepszą jakość niż te, które nie, a nie charakteryzują się krawędzie symptomem — lub "otoczki efekt" — efekcie podczas blend tekstury, które nie używają wstępnie przemnożone alfa.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Aby utworzyć tekstury, która używa wstępnie przemnożone alfa

1.  Rozpoczynać się od podstawowego tekstury. Załadować istniejący plik obrazu lub utworzyć zgodnie z opisem w [porady: Tworzenie podstawowego tekstury](../designers/how-to-create-a-basic-texture.md).

2.  Konfigurowanie pliku tekstury tak, aby jest przetwarzany przez potok zawartości obrazu. W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku tekstury, a następnie wybierz pozycję **właściwości**. Na **właściwości konfiguracji**, **ogólne** ustaw **typu elementu** właściwości **potoku zawartości obrazu**. Upewnij się, że **zawartości** właściwość jest ustawiona na **tak** i **wykluczyć z kompilacji** ma ustawioną wartość **nr**, a następnie wybierz pozycję  **Zastosuj** przycisku. **Potoku zawartości obrazu** zostanie wyświetlona strona właściwości konfiguracji.

3.  Konfiguruje potok zawartości obrazu do generowania wstępnie przemnożone alfa. Na **właściwości konfiguracji**, **potoku zawartości obrazu**, **ogólne** ustaw **skonwertować do formatu alfa wstępnie pomnożonych** dla właściwości **tak (/ generatepremultipliedalpha)**.

4.  Wybierz **OK** przycisku.

 Podczas kompilowania projektu potoku zawartości obrazu konwertuje obraz źródłowy pracy określony format wyjściowy — dotyczy to również Konwersja obrazu do wstępnie przemnożone formatu alfa — a wynik jest kopiowana do danych wyjściowych projektu katalog.