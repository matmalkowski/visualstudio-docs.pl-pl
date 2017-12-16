---
title: "Porady: Tworzenie typów za pomocą projektanta klas | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b6bd8420a56e20e5cb2fb04bd47931bae68207d1
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2017
---
# <a name="how-to-create-types-by-using-class-designer"></a>Porady: tworzenie typów za pomocą Projektanta klas
Projektowanie nowych typów dla projektów Visual Basic .NET i Visual C# .NET, należy je utworzyć na diagramie klas. Aby wyświetlić istniejące typy, zobacz [porady: wyświetlanie istniejących typów](how-to-view-existing-types.md).  
  
-   [Utwórz nowy typ](#CreateType)  
  
-   [Zastosuj do typu atrybutu niestandardowego](#CustAttributeType)  
  
-   [Zastosuj atrybut niestandardowy do elementu członkowskiego typu](#CustAttributeMember)  
  
##  <a name="CreateType"></a>Utwórz nowy typ  
  
1.  W przyborniku, w obszarze Projektanta klas przeciągnij jeden z nich do diagramu klasy:  
  
    -   **Klasa** lub **klasy abstrakcyjnej**  
  
    -   **Wyliczenia**  
  
    -   **Interfejs**  
  
    -   **Struktura** (VB) lub **struktury** (C#)  
  
    -   **Delegat**  
  
    -   **Moduł** (tylko VB)  
  
2.  Nadaj nazwę typowi. Następnie wybierz jego poziom dostępu.  
  
3.  Wybierz plik, do którego chcesz dodać kod początkowy dla typu:  
  
    -   Aby utworzyć nowy plik i dodać ją do bieżącego projektu, zaznacz **Utwórz nowy plik** i nazwę pliku.  
  
    -   Aby dodać kod do istniejącego pliku, wybierz **dodać do istniejącego pliku**.  
  
         Jeśli rozwiązanie zawiera projekt, który udostępnia kod wielu aplikacjom, możesz dodać nowy typ do diagramu klas do projektu aplikacji, ale tylko jeśli odpowiedni plik klasa znajduje się w tym samym projekcie aplikacji lub znajduje się w projekcie udostępnionym.  
  
4.  Teraz dodaj inne elementy, aby zdefiniować typ:  
  
    |||  
    |-|-|  
    |**Dla**|**Dodaj**|  
    |Klasy, klasy abstrakcyjne, struktury i obiekty struct|Metody, właściwości, pola, zdarzenia, konstruktory (metoda), destruktory (metoda) i stałe, które określają typ|  
    |Wyliczenia|Wartości pól, które tworzą wyliczenie|  
    |Interfejsy|Metody, właściwości i zdarzenia, które tworzą interfejs|  
    |Delegate|Parametry, które definiują obiekt delegowany|  
    |Moduł|Metody, właściwości, pola, zdarzenia, konstruktory (metoda) i stałe, które określają moduł|  
  
     Zobacz [tworzenia elementów członkowskich](creating-and-configuring-type-members.md#CreateMembers).  
  
##  <a name="CustAttributeType"></a>Zastosuj do typu atrybutu niestandardowego  
  
1.  Kliknij typ kształtu na diagramie klasy.  
  
2.  W oknie właściwości obok **atrybuty niestandardowe** właściwości dla typu, kliknij przycisk wielokropka (...).  
  
3.  Dodaj jeden lub więcej atrybutów niestandardowych, jeden na wiersz. Nie otaczaj ich nawiasami kwadratowymi.  
  
     Kiedy skończysz, atrybuty niestandardowe są stosowane do typu.  
  
##  <a name="CustAttributeMember"></a>Zastosuj atrybut niestandardowy do elementu członkowskiego typu  
  
1.  Kliknij nazwę składowej w jej kształcie typu na diagramie klasy lub kliknij jej wiersz w oknie Szczegóły klasy.  
  
2.  W oknie właściwości można znaleźć elementu członkowskiego **atrybuty niestandardowe** właściwości.  
  
3.  Dodaj jeden lub więcej atrybutów niestandardowych, jeden na wiersz. Nie otaczaj ich nawiasami kwadratowymi.  
  
     Kiedy skończysz, atrybuty niestandardowe są stosowane do typu.  
  
## <a name="see-also"></a>Zobacz także
[Porady: Tworzenie dziedziczenia pomiędzy typami](how-to-create-inheritance-between-types.md)  
[Porady: Tworzenie skojarzenia między typami](how-to-create-associations-between-types.md)
[tworzenie i konfigurowanie typów członków](creating-and-configuring-type-members.md)   
[Praca z diagramami klas](working-with-class-diagrams.md)   
[Projektowanie klas i typów](designing-classes-and-types.md)