---
title: Hierarchia wywołań | Dokumentacja firmy Microsoft
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
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
ms.assetid: c55bda01-d7de-4823-8f9a-1bcc37dbb74a
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 212109c37e1c85d5ddbc55413ab5a972edbfa337
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775195"
---
# <a name="call-hierarchy"></a>Hierarchia wywołań
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [hierarchię wywołań,](https://docs.microsoft.com/visualstudio/ide/reference/call-hierarchy).  
  
  
Hierarchię wywołań umożliwia nawigowanie po kodzie, wyświetlając wszystkie wywołania do i z wybranej metody, właściwości lub konstruktora. Dzięki temu można lepiej zrozumieć przepływ kodu i oceny wpływu zmian kodu. Można sprawdzić kilka poziomów kodem, aby wyświetlić złożonych łańcuchy wywołania metody oraz dodatkowe punkty wejścia do kodu, który umożliwia poznawanie wszystkie możliwe wykonania ścieżki.  
  
 Hierarchię wywołań jest dostępna w czasie projektowania, w przeciwieństwie do stosu wywołań, które jest wyświetlane przez debuger.  
  
## <a name="using-call-hierarchy"></a>Za pomocą hierarchię wywołań  
 Aby wyświetlić **hierarchię wywołań,** , kliknij prawym przyciskiem myszy nazwę metody, właściwości lub wywołanie konstruktora, a następnie kliknij przycisk **Pokaż hierarchię wywołań,**.  
  
 Nazwa elementu członkowskiego, który pojawia się w okienku widoku drzewa, w **hierarchię wywołań** okna. Po rozwinięciu węzła elementu członkowskiego **wywołania do**_nazwa elementu członkowskiego_ i **wywołania z**_nazwa elementu członkowskiego_ węzły podrzędne są wyświetlane. Poniższa ilustracja przedstawia te węzły w **hierarchię wywołań** okna.  
  
 ![Hierarchia wywołań z jednym węzłem, otwórz](../../ide/reference/media/onenode.png "OneNode")  
Okno hierarchii wywołań  
  
-   Po rozwinięciu **wywołania do** węzeł, wszystkie elementy członkowskie, że wyświetlane są wywołania wybranego elementu członkowskiego.  
  
-   Po rozwinięciu **wywołania z** są wyświetlane w węźle wszystkie elementy członkowskie, które są wywoływane przez wybrany element członkowski.  
  
 Następnie można rozwiń każdą z tych węzłów podrzędnych elementów członkowskich, do **wywołania do** i **wywołania z** węzłów. Dzięki temu można nawigować do stosu wywołań, jak pokazano na poniższej ilustracji.  
  
 ![Hierarchia wywołań z otwartymi wieloma węzłami](../../ide/media/multiplenodes.png "MultipleNodes")  
Okno hierarchii wywołań  
  
 Dla elementów członkowskich, które są zdefiniowane jako wirtualny lub abstrakcyjnej **nazwę metody zastąpienia** węzeł jest dostępny. Dla członków interfejsu **nazwę metody implementuje** węzeł jest dostępny. Te węzły można rozwijać pojawiają się na tym samym poziomie co **wywołania do** i **wywołania z** węzłów.  
  
 **Zakres wyszukiwania** na pasku narzędzi zawiera opcje dla **Moje rozwiązanie**, **bieżący projekt**, i **bieżący dokument**.  
  
 Po wybraniu podrzędny element członkowski w **hierarchię wywołań** okienku widoku drzewa:  
  
-   **Hierarchię wywołań** okienku szczegółów zostaną wyświetlone wszystkie wiersze kodu, w którym ten podrzędny element członkowski jest wywoływana z nadrzędnego elementu członkowskiego.  
  
-   **Okno definicji kodu**, jeśli jest otwarty, wyświetlany jest kod dla wybranego elementu członkowskiego. W tym oknie jest dostępna w języku C# i C++. Aby uzyskać więcej informacji na temat tego okna, zobacz [wyświetlanie struktury kodu](../../ide/viewing-the-structure-of-code.md).  
  
> [!NOTE]
>  Hierarchię wywołań nie odnajdzie metoda odwołania do grupy, w tym miejsca, w którym metoda jest dodawana jako procedura obsługi zdarzeń lub jest przypisany do delegata. Aby znaleźć wszystkie odwołania do metody, można użyć **Znajdź wszystkie odwołania** polecenia.  
  
## <a name="shortcut-menu-items"></a>Elementy Menu skrótów  
 W poniższej tabeli opisano kilka opcji menu skrótów, które są dostępne po kliknięciu prawym przyciskiem myszy węzeł w okienku widoku drzewa.  
  
|W Menu kontekstowym|Opis|  
|-----------------------|-----------------|  
|**Dodaj jako nowy element główny**|Dodaje wybrany węzeł w okienku widoku drzewa jako nowy węzeł główny. Dzięki temu można skoncentrować się uwagi na określonych poddrzewo.|  
|**Usuń element główny**|Usuwa wybrany główny węzeł, w okienku widoku drzewa. Ta opcja jest dostępna tylko z węzła głównego.<br /><br /> Można również użyć **Usuń głównego** przycisku paska narzędzi, aby usunąć węzeł główny wybrane.|  
|**Przejdź do definicji**|Uruchamia polecenie Przejdź do definicji dla wybranego węzła. Powoduje to przejście do oryginalnej definicji dla wywołania elementu członkowskiego lub definicji zmiennej.<br /><br /> Aby wykonać polecenie Przejdź do definicji, możesz kliknąć dwukrotnie wybrany węzeł lub nacisnąć klawisz F12, dla wybranego węzła.|  
|**Znajdź wszystkie odwołania**|Uruchamia polecenie Znajdź wszystkie odwołania dla wybranego węzła. To umożliwia znalezienie wszystkich wierszy kodu w projekcie tego odwołanie do klasy lub elementu członkowskiego.<br /><br /> SHIFT + F12 umożliwia również Uruchom polecenie Znajdź wszystkie odwołania dla wybranego węzła.|  
|**Kopiuj**|Kopiuje zawartość wybranego węzła (ale nie jego węzły podrzędne).|  
|**Odśwież**|Zwija wybrany węzeł, aby ponownie powiększający się Wyświetla bieżące informacje.|



