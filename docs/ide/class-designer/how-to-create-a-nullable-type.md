---
title: 'Porady: Tworzenie typu Zerowalnego (Projektant klas) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fcef9fc80bbc55b07cd9dad68e217c9982a3b1f7
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-create-a-nullable-type-class-designer"></a>Porady: tworzenie typu zerowalnego (Projektant klas)
Niektórych typów wartości nie zawsze mieć lub muszą zdefiniowanej wartości. Jest typowym rozwiązaniem w przypadku baz danych, gdy niektóre pola nie można przypisać wartości. Na przykład można przypisać wartości null na wskazują, że jej nie został jeszcze przypisany wartość pole bazy danych.  
  
A *typ dopuszczający wartość null* jest typem wartości, które można rozszerzyć, aby przyspieszyć typowe zakres wartości dla tego typu, a także wartość null. Na przykład wartości null z `Int32`, również oznaczane jako wartości null\<Int32 > można przypisać wartości od -2147483648 do 2147483647 i można do niej przypisywać wartości null. Typu Nullable\<bool > można przypisać wartości `True`, `False`, lub wartość null (Brak wartości we wszystkich).  
  
Typy dopuszczające wartości null są wystąpieniami klasy <xref:System.Nullable%601> struktury. Każde wystąpienie typu dopuszczającego wartości null ma dwa publicznej właściwości tylko do odczytu, `HasValue` i `Value`:  
  
-   `HasValue`Typ jest `bool` i wskazuje, czy zmienna zawiera zdefiniowanej wartości. `True`oznacza, że zmienna zawiera wartość inną niż null. Możesz przetestować zdefiniowanych wartości przy użyciu instrukcji, takich jak `if (x.HasValue)` lub `if (y != null)`.  
  
-   `Value`jest tego samego typu jako typu bazowego. Jeśli `HasValue` jest `True`, `Value` zawiera odpowiednią wartość. Jeśli `HasValue` jest `False`, podczas uzyskiwania dostępu do `Value` spowoduje zgłoszenie wyjątku Nieprawidłowa operacja.  
  
Domyślnie w deklaracji zmiennej jako wartości null typu go nie ma zdefiniowanej wartości (`HasValue` jest `False`), inne niż domyślna wartość jego typem podstawowym wartość.  
  
Projektant klas Wyświetla typ dopuszczający wartość null, tak samo, jak wyświetla jego typem podstawowym.  
  
Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe w języku C#, zobacz [typy dopuszczające wartości zerowe](/dotnet/csharp/programming-guide/nullable-types/index). Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe w języku Visual Basic, zobacz [typy dopuszczające wartości zerowe wartości](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).  
  
[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Aby dodać typ dopuszczający wartość null, za pomocą projektanta klas  
  
1.  Na diagramie klas rozwiń istniejącej klasy lub Utwórz nową klasę.  
  
2.  Aby dodać klasę do projektu, na **diagramu klas** menu, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.  
  
3.  Aby rozwinąć kształt klasa na **diagramu klas** menu, kliknij przycisk **rozwiń**.  
  
4.  Wybierz kształt klasy. Na **diagramu klas** menu, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **pola**. Nowe pole o nazwie domyślnej **pola** będą wyświetlane w kształtu klasy, a także w **szczegółów klasy** okna.  
  
5.  W **nazwa** kolumny **szczegółów klasy** okna (lub w klasie kształtu, sam), Zmień nazwę nowego pola na prawidłową i łatwy do rozpoznania nazwy.  
  
6.  W **typu** kolumny **szczegółów klasy** okna, należy zadeklarować typ jako typ dopuszczający wartość null, jak pokazano w poniższym kodzie:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Aby dodać typ dopuszczający wartość null, za pomocą edytora kodu  
  
1.  Dodaj klasę do projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **Dodaj klasę**.  
  
2.  W pliku .cs lub .vb dla nowej klasy należy dodać co najmniej jeden typ dopuszczający wartość null w nowej klasy do deklaracji klasy.  
  
3.  Z widoku klasy przeciągnij ikonę nowe klasy powierzchnię projektanta klas. Kształt klasy pojawia się na diagramie klas.  
  
4.  Rozwiń szczegóły dla kształtu klasy i przesuń wskaźnik myszy nad elementów członkowskich klasy. Etykietka narzędzia wyświetlana deklaracji dla każdego elementu członkowskiego.  
  
5.  Kliknij prawym przyciskiem myszy kształtu klasy, a następnie kliknij przycisk **szczegółów klasy**. Można wyświetlać lub modyfikować nowy typ właściwości w **szczegółów klasy** okna.  
  
## <a name="see-alose"></a>Zobacz alose
<xref:System.Nullable%601>   
[Typy dopuszczające wartości zerowe](/dotnet/csharp/programming-guide/nullable-types/index)   
[Przy użyciu typów dopuszczających wartości zerowe](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)   
[Porady: Identyfikowanie typu dopuszczającego wartość null](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)   
[Typy wartości dopuszczających wartości null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)