---
title: "Hierarchia wywołań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.CallHierarchy
helpviewer_keywords: Call Hierarchy
ms.assetid: c55bda01-d7de-4823-8f9a-1bcc37dbb74a
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4aed087f8280049018818e68f7db56960db7e690
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="call-hierarchy"></a>Hierarchia wywołań
Hierarchia wywołań pozwala poruszać się po kodzie za pomocą wyświetlania wszystkich wywołań do i z wybranej metody, właściwości lub konstruktora. Dzięki temu można lepiej zrozumieć, jak przepływu kodu oraz ocena skutków zmiany kodu. Można sprawdzić kilka poziomów kod, aby wyświetlić złożonych łańcuchów wywołań metod i dodatkowe punkty wejścia do kodu, dzięki czemu można eksplorować wszystkie możliwe wykonanie ścieżki.  
  
 Hierarchia wywołań jest dostępne w czasie projektowania, w odróżnieniu od stos wywołań, który jest wyświetlany przez debuger.  
  
## <a name="using-call-hierarchy"></a>Za pomocą hierarchii wywołań  
 Aby wyświetlić **hierarchii wywołań** , kliknij prawym przyciskiem myszy nazwę metoda, właściwość lub wywołanie konstruktora, a następnie kliknij przycisk **hierarchii wywołań widoku**.  
  
 Nazwa elementu członkowskiego jest wyświetlana w okienku widoku drzewa, w **hierarchii wywołań** okna. Po rozwinięciu węzła elementu członkowskiego **wywołania do***nazwa elementu członkowskiego* i **wywołania z***nazwa elementu członkowskiego* węzły podrzędne są wyświetlane. Na poniższej ilustracji przedstawiono te węzły w **hierarchii wywołań** okna.  
  
 ![Hierarchia wywołań z jednym węzłem, otwórz](../../ide/reference/media/onenode.png "OneNode")  
Okno hierarchii wywołań  
  
-   Po rozwinięciu **wywołania do** węzła, że wywołanie wybrany element członkowski są wyświetlane wszystkie elementy członkowskie.  
  
-   Po rozwinięciu **wywołania z** są wyświetlane w węźle wszystkie elementy członkowskie, które są wywoływane przez wybrany element członkowski.  
  
Następnie można rozwinąć każdego z tych elementów członkowskich podwęzłem do **wywołania do** i **wywołania z** węzłów. Dzięki temu można nawigować do stosu wywołań, jak pokazano na poniższej ilustracji.  
  
![Hierarchia wywołań otwartymi wieloma węzłami](../../ide/media/multiplenodes.png "MultipleNodes")  
Okno hierarchii wywołań  
  
Dla elementów członkowskich, które są zdefiniowane jako wirtualny lub abstrakcyjny **nazwę metody zastąpienia** węzeł jest dostępny. Dla członków interfejsu **nazwę metody implementuje** węzeł jest dostępny. Te węzły rozwijania są wyświetlane na tym samym poziomie jako **wywołania do** i **wywołania z** węzłów.  
  
**Zakres wyszukiwania** na pasku narzędzi zawiera opcje **Moje rozwiązanie**, **bieżącego projektu**, i **bieżącego dokumentu**.  
  
Po wybraniu podrzędny element członkowski w **hierarchii wywołań** okienka widoku drzewa:  
  
-   **Hierarchii wywołań** okienku szczegółów zostaną wyświetlone wszystkie wiersze kodu, w którym ten podrzędny element członkowski jest wywoływana z nadrzędnego elementu członkowskiego.  
  
-   **Okno definicji kodu**, jeśli jest to otwarty, wyświetla kod dla wybranego elementu członkowskiego. To okno jest dostępna w C# i C++. Aby uzyskać więcej informacji dotyczących tego okna, zobacz [wyświetlanie struktury kodu](../../ide/viewing-the-structure-of-code.md).  
  
> [!NOTE]
>  Hierarchii wywołań nie odnajdzie — metoda odwołania do grup, w tym miejscach, gdzie metoda jest dodawana jako program obsługi zdarzeń lub jest przypisany do delegata. Aby znaleźć wszystkie odwołania do metody, można użyć **Znajdź wszystkie odwołania** polecenia.  
  
## <a name="shortcut-menu-items"></a>Elementy Menu skrótów  
 W poniższej tabeli opisano kilka opcji menu skrótów, które są dostępne po kliknięciu prawym przyciskiem myszy węzeł w okienku widoku drzewa.  
  
|W Menu kontekstowym|Opis|  
|-----------------------|-----------------|  
|**Dodaj jako nowy element główny**|Dodaje wybrany węzeł w okienku widoku drzewa, jako nowego węzła głównego. Dzięki temu można koncentrować w określonym poddrzewie.|  
|**Usuwanie głównego**|Usuwa wybrany główny węzeł w okienku widoku drzewa. Ta opcja jest dostępna wyłącznie z węzła głównego.<br /><br /> Można również użyć **usunąć głównego** przycisku paska narzędzi, aby usunąć wybrany główny węzeł.|  
|**Przejdź do definicji**|Uruchamia polecenie Przejdź do definicji dla wybranego węzła. Powoduje to przejście do oryginalnej definicji dla wywołania elementu członkowskiego lub definicji zmiennej.<br /><br /> Aby uruchomić polecenie Przejdź do definicji, możesz dwukrotnie kliknij wybrany węzeł lub naciśnij klawisz F12, dla wybranego węzła.|  
|**Znajdź wszystkie odwołania**|Uruchamia polecenie Znajdź wszystkie odwołania dla wybranego węzła. Znajduje to wierszy kodu w projekcie tego odwołania klasy lub elementu członkowskiego.<br /><br /> SHIFT + F12 umożliwia również uruchomić polecenie Znajdź wszystkie odwołania dla wybranego węzła.|  
|**Kopiuj**|Kopiuje zawartość wybranego węzła (ale nie jego węzłami podrzędnymi).|  
|**Odśwież**|Zwija wybrany węzeł, aby ponownie rozszerzanie on Wyświetla bieżące informacje.|