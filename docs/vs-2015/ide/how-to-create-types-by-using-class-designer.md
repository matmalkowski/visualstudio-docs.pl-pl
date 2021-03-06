---
title: 'Porady: Tworzenie typów za pomocą projektanta klas | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f7671b1336b0b722f02cc100c7055fef817cb582
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685578"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Porady: tworzenie typów za pomocą Projektanta klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Tworzenie typów za pomocą projektanta klas](https://docs.microsoft.com/visualstudio/ide/how-to-create-types-by-using-class-designer).  
  
Do projektowania nowych typów projektów Visual Basic .NET i Visual C# .NET, należy je utworzyć na diagramie klasy. Aby wyświetlić istniejące typy, zobacz [porady: wyświetlanie istniejących typów (Projektant klas)](../ide/how-to-view-existing-types-class-designer.md).  
  
-   [Utwórz nowy typ](#CreateType)  
  
-   [Zastosuj atrybut niestandardowy do typu](#CustAttributeType)  
  
-   [Zastosuj atrybut niestandardowy do elementu członkowskiego typu](#CustAttributeMember)  
  
##  <a name="CreateType"></a> Utwórz nowy typ  
  
1.  W przyborniku, w obszarze Projektanta klas przeciągnij jeden z nich do diagramu klasy:  
  
    -   **Klasa** lub **klasy abstrakcyjnej**  
  
    -   **Enum**  
  
    -   **Interface**  
  
    -   **Struktura** (VB) lub **struktury** (C#)  
  
    -   **Delegate**  
  
    -   **Moduł** (tylko w języku VB)  
  
2.  Nadaj nazwę typowi. Następnie wybierz jego poziom dostępu.  
  
3.  Wybierz plik, do którego chcesz dodać kod początkowy dla typu:  
  
    -   Aby utworzyć nowy plik i dodać go do bieżącego projektu, wybierz **Utwórz nowy plik** i nazwę pliku.  
  
    -   Aby dodać kod do istniejącego pliku, wybierz **Dodaj do istniejącego pliku**.  
  
         Jeśli rozwiązanie ma projektu, który udostępnia kod przez wiele aplikacji, możesz dodać nowy typ do diagramu klas w projekcie aplikacji, ale tylko jeśli odpowiadający plik klasy znajduje się w tym samym projekcie aplikacji lub znajduje się w udostępnionym projekcie.  
  
4.  Teraz dodaj inne elementy, aby zdefiniować typ:  
  
    |||  
    |-|-|  
    |**Aby uzyskać**|**Dodaj**|  
    |Klasy, klasy abstrakcyjne, struktury i obiekty struct|Metody, właściwości, pola, zdarzenia, konstruktory (metoda), destruktory (metoda) i stałe, które określają typ|  
    |Wyliczenia|Wartości pól, które tworzą wyliczenie|  
    |Interfejsy|Metody, właściwości i zdarzenia, które tworzą interfejs|  
    |Delegate|Parametry, które definiują obiekt delegowany|  
    |Moduł|Metody, właściwości, pola, zdarzenia, konstruktory (metoda) i stałe, które określają moduł|  
  
     Zobacz [tworzenie elementów członkowskich](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
##  <a name="CustAttributeType"></a> Zastosuj atrybut niestandardowy do typu  
  
1.  Kliknij typ kształtu na diagramie klasy.  
  
2.  W oknie dialogowym właściwości obok **atrybuty niestandardowe** właściwości dla typu, kliknij przycisk wielokropka (...).  
  
3.  Dodaj jeden lub więcej atrybutów niestandardowych, jeden na wiersz. Nie otaczaj ich nawiasami kwadratowymi.  
  
     Kiedy skończysz, atrybuty niestandardowe są stosowane do typu.  
  
##  <a name="CustAttributeMember"></a> Zastosuj atrybut niestandardowy do elementu członkowskiego typu  
  
1.  Kliknij nazwę składowej w jej kształcie typu na diagramie klasy lub kliknij jej wiersz w oknie Szczegóły klasy.  
  
2.  W oknie właściwości Znajdź elementu członkowskiego **atrybuty niestandardowe** właściwości.  
  
3.  Dodaj jeden lub więcej atrybutów niestandardowych, jeden na wiersz. Nie otaczaj ich nawiasami kwadratowymi.  
  
     Kiedy skończysz, atrybuty niestandardowe są stosowane do typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie dziedziczenia między typami (Projektant klas)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Porady: Tworzenie skojarzeń między typami (Projektant klas)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Tworzenie i konfigurowanie składowych typu (Projektant klas)](../ide/creating-and-configuring-type-members-class-designer.md)   
 [Praca z diagramami klas (Projektant klas)](../ide/working-with-class-diagrams-class-designer.md)   
 [Projektowanie klas i typów (Projektant klas)](../ide/designing-classes-and-types-class-designer.md)



