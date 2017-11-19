---
title: Korzystanie z IntelliSense | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.tools.intellisense
helpviewer_keywords:
- IntelliSense, Complete Word
- IntelliSense, completion mode
- parameter information
- IntelliSense, List Members
- Quick Info
- Parameter Info
- IntelliSense [Visual Studio]
- IntelliSense, suggestion mode
- IntelliSense, Parameter Info
- IntelliSense, customizing
- Complete Word
- IntelliSense
- List Members
ms.assetid: 9fdb489b-8b46-4b92-9ccc-c8f8cc184081
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 149cb62f35ce4b1ce15ab939a0805bc63bfb6f26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="using-intellisense"></a>Korzystanie z IntelliSense
Technologia IntelliSense jest ogólnym terminem dla wielu funkcji: elementów członkowskich listy, informacji o parametrach, szybkich informacji i uzupełniania słów. Te funkcje pozwalają dowiedzieć się więcej o kodzie, którego używasz, śledzić wpisywane parametry i dodawać wywołania do właściwości i metod za pomocą zaledwie kilku naciśnięć klawiszy.  
  
 Wiele aspektów IntelliSense jest specyficzne dla języków. Aby uzyskać więcej informacji na temat technologii IntelliSense dla różnych języków, zobacz tematy wymienione w sekcji Zobacz też.  
  
## <a name="list-members"></a>Lista składników  
 Zostanie wyświetlona lista elementów prawidłową z typu (lub przestrzeni nazw), po wpisaniu znaku wyzwalacza (na przykład okres (`.`) w kodzie zarządzanym lub `::` w języku C++). Jeśli będziesz kontynuować, wpisując znaków, lista jest filtrowana do uwzględnienia tylko do elementów członkowskich, które zaczynają się od tych znaków lub których na początku *żadnych* programu word w nazwa rozpoczyna się od tych znaków. IntelliSense wykonuje także "camelcase" dopasowania, więc można po prostu wpisz pierwszą literę każdego wyrazu formatu — z uwzględnieniem wielkości liter w nazwie elementu członkowskiego, aby zobaczyć dopasowań.   
  
 Po wybraniu elementu, wstaw go do kodu za pomocą klawisza TAB lub wciśnięcia spacji. Jeśli wybierzesz element i wpiszesz kropkę, element pojawia się, a po nim kropka, co wywołuje kolejną listę elementów członkowskich. Po wybraniu elementu, ale przed jego wstawieniem, otrzymasz szybkie informacje na jego temat.  
  
 Na liście elementów członkowskich ikona po lewej stronie reprezentuje typ elementu członkowskiego, taki jak przestrzeń nazw, klasa, funkcja lub zmienna. Listę ikony, zobacz [Widok klas i przeglądarka obiektów ― ikony](../ide/class-view-and-object-browser-icons.md). Lista może być dość długa, więc można nacisnąć klawisz PAGE UP lub PAGE DOWN, aby przejść w górę lub w dół na liście.  
  
 ![Lista elementów członkowskich programu Visual Studio](../ide/media/vs2015_intellisense.png "vs2015_Intellisense")  
  
 Można wywołać **członków listy** funkcji, ręcznie wpisując CTRL + J, klikając pozycję **IntelliSense/edytowanie/listy członków**, lub klikając **członków listy** przycisk w edytorze pasek narzędzi. Gdy jest wywoływana w pustym wierszu lub poza rozpoznawalnym zasięgiem, na liście wyświetlane są symbole w globalnej przestrzeni nazw.  
  
 Aby wyłączyć członków listy domyślnie (tak aby nie jest wyświetlana, jeśli wywołania), przejdź do **narzędzia/Opcje/wszystkie języki** i usuń zaznaczenie **automatyczna lista członków**. Jeśli chcesz wyłączyć członków listy tylko dla określonego języka, przejdź do **ogólne** ustawień dla tego języka.  
  
 Można również przejść do trybu sugestii, w którym tylko wpisany tekst jest umieszczony w kodzie. Na przykład, jeśli wpiszesz identyfikator, który nie jest na liście, i naciśniesz klawisz TAB, w trybie uzupełniania wpis zastąpi wpisany identyfikator. Aby przełączyć tryb uzupełniania i tryb sugestii, naciśnij kombinację klawiszy CTRL + ALT + SPACJA, lub kliknij przycisk **edycji/IntelliSense/Przełącz tryb uzupełniania**.  
  
## <a name="parameter-info"></a>Informacje o parametrach  
 Informacje o parametrach zawierają informacje na temat liczby, nazw i typów parametrów wymaganych przez metodę, parametr typu ogólnego atrybutu (w języku C#) lub szablon (w języku C++).  
  
 Parametr pogrubiony wskazuje następny parametr, który jest wymagany podczas wprowadzania funkcji. Dla przeciążonych funkcji klawisze strzałek w górę i w dół umożliwiają wyświetlenie informacji o alternatywnych parametrach przeciążeń funkcji.  
  
 ![Informacje o parametrach](../ide/media/vs2015_param_info.png "VS2015_param_Info")  
  
 Gdy opisujesz funkcje i parametry za pomocą komentarzy dokumentacji XML, komentarze będą wyświetlane jako informacje o parametrach. Aby uzyskać więcej informacji, zobacz [dostarczanie komentarze w kodzie XML](../ide/supplying-xml-code-comments.md).  
  
 Informacje o parametrach można wywołać ręcznie, klikając **Edytuj informacje funkcji IntelliSense i parametru**, wpisując polecenie CTRL + SHIFT + SPACJA lub kliknięcie **informacje o parametrach** przycisk na pasku narzędzi edytora.  
  
## <a name="quick-info"></a>Szybkie informacje  
 Szybkie informacje wyświetlają pełną deklarację dla każdego identyfikatora w kodzie.  
  
 ![Szybkie informacje programu Visual Studio](../ide/media/vs2015_quick_info.png "VS2015_Quick_info")  
  
 Po wybraniu elementu członkowskiego **członków listy** polu Szybkie informacje jest także wyświetlany.  
  
 ![Informacje o parametrach w C & 35; plik kodu](../ide/media/vs2015_paraminfo.png "VS2015_ParamInfo")  
  
 Szybkie informacje można wywołać ręcznie, klikając **edycji/IntelliSense/szybkie informacje**, wpisując polecenie CTRL + I lub kliknięcie **szybka podpowiedź** przycisk na pasku narzędzi edytora.  
  
 Jeżeli funkcja jest przeciążona, mechanizm IntelliSense może nie wyświetlać informacji dla wszystkich postaci przeciążenia.  
  
 Szybkie informacje off w C++ można włączyć, ustawiając **narzędzia / Opcje / Edytor tekstu/C/C + +/ zaawansowane/automatyczna szybka podpowiedź** do `false`.  
  
## <a name="complete-word"></a>Dokończ wyraz  
 Dokończ wyraz uzupełnia pozostałą część zmiennej, polecenia lub nazwy funkcji, po wprowadzeniu dostatecznej liczby znaków, aby odróżnić termin. Całe słowo może wywołać klikając **Word Complete-edycji/IntelliSense**, wpisując polecenie CTRL + SPACJA, lub kliknięcie **całe słowo** przycisk na pasku narzędzi edytora.  
  
## <a name="intellisense-options"></a>Opcje IntelliSense  
 Opcje IntelliSense są domyślnie włączone. Aby je wyłączyć, kliknij przycisk **narzędzia/Opcje/tekstu edytor** i usuń zaznaczenie **informacje o parametrach** lub **automatyczna lista członków** Jeśli nie chcesz, aby funkcja listy członków.  
  
## <a name="troubleshooting-intellisense"></a>Rozwiązywanie problemów z technologią IntelliSense  
 W niektórych przypadkach opcje IntelliSense mogą nie działać zgodnie z oczekiwaniami.  
  
 **Gdy kursor znajduje się poniżej błąd kodu.** Nie można używać funkcji IntelliSense, jeśli funkcja niekompletne lub inny błąd nie istnieje w kodzie powyżej kursora, ponieważ nie można zanalizować elementy kodu IntelliSense. Można naprawić ten problem, zakomentowując odpowiedni kod.  
  
 **Kursor znajduje się w komentarz do kodu.** Nie można użyć funkcji IntelliSense, jeśli kursor znajduje się w komentarzu w pliku źródłowym.  
  
 **Kursor jest literałem ciągu.** Nie można użyć funkcji IntelliSense, gdy kursor znajduje się w cudzysłowie literału ciągu, jak w poniższym przykładzie:  
  
```  
MessageBox( hWnd, "String literal|")
```  
  
 **Opcje automatycznego są wyłączone.** Domyślnie IntelliSense działa automatycznie, ale można ją wyłączyć. Nawet jeśli automatyczne uzupełnianie instrukcji jest wyłączone, można wywołać funkcję mechanizmu IntelliSense.  
  
## <a name="see-also"></a>Zobacz też  
 [IntelliSense specyficzne dla języka Visual Basic](../ide/visual-basic-specific-intellisense.md)   
 [Visual C#, IntelliSense](../ide/visual-csharp-intellisense.md)   
 [IntelliSense dla JavaScript](../ide/javascript-intellisense.md)   
 [Stosowanie komentarzy kodu XML](../ide/supplying-xml-code-comments.md)
