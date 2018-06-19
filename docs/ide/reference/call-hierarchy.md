---
title: Znajdź wywołania do metody
ms.date: 05/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52fdaf277d8c20801c5d48d90de472d24ab88bda
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448353"
---
# <a name="view-call-hierarchy"></a>Wyświetlanie hierarchii wywołań

Wyświetlając hierarchii wywołań do kodu, można przejść wszystkie wywołania do i czasami od wybranej metody, właściwości lub konstruktora. Dzięki temu można lepiej zrozumieć, jak przepływu kodu oraz ocena skutków zmiany kodu. Można sprawdzić kilka poziomów kod, aby wyświetlić złożonych łańcuchów wywołań metod i dodatkowe punkty wejścia do kodu. Dzięki temu można eksplorować wszystkie możliwe wykonanie ścieżki.

W programie Visual Studio można wyświetlić hierarchię wywołań w czasie projektowania. Oznacza to, że nie trzeba ustawić punkt przerwania i uruchomić debugera, aby wyświetlić stos wywołań w czasie wykonywania.

## <a name="use-the-call-hierarchy-window"></a>Okno hierarchii wywołań

Aby wyświetlić **hierarchii wywołań** , kliknij prawym przyciskiem myszy w edytorze kodu na nazwę metody, właściwość lub wywołanie konstruktora, a następnie wybierz **hierarchii wywołań widoku**.

Nazwa elementu członkowskiego jest wyświetlana w okienku widoku drzewa, w **hierarchii wywołań** okna. Po rozwinięciu węzła elementu członkowskiego **wywołania do** *nazwa elementu członkowskiego*, a dla języka C++, **wywołania z** *nazwa elementu członkowskiego*, węzły podrzędne są wyświetlane.

Dla kodu C++ można wyświetlić połączeń zarówno do i z elementu członkowskiego:

![Hierarchia wywołań kodu C++ w programie Visual Studio](media/call-hierarchy-cpp.png)

C# i Visual Basic code możesz zobaczyć wywołania do elementu członkowskiego, ale nie wywołania z:

![Hierarchia wywołań dla kodu C# w programie Visual Studio](media/call-hierarchy-csharp.png)

- Po rozwinięciu **wywołania do** węzła, że wywołanie wybrany element członkowski są wyświetlane wszystkie elementy członkowskie.

- Dla języka C++, f rozwinięciu **wywołania z** są wyświetlane w węźle wszystkie elementy członkowskie, które są wywoływane przez wybrany element członkowski.

Następnie rozwiń węzeł każdego wywołania elementu członkowskiego, aby zobaczyć jego **wywołania do**, a dla języka C++, **wywołania z** węzłów. Dzięki temu można nawigować do stosu wywołań, jak pokazano na poniższej ilustracji:

![Okno hierarchii wywołań o różnych poziomach rozwinięty](media/call-hierarchy-csharp-expanded.png)

Dla elementów członkowskich, które są zdefiniowane jako wirtualny lub abstrakcyjny **nazwę metody zastąpienia** węzeł jest dostępny. Dla członków interfejsu **nazwę metody implementuje** węzeł jest dostępny. Te węzły rozwijania są wyświetlane na tym samym poziomie jako **wywołania do** i **wywołania z** węzłów.

**Zakres wyszukiwania** na pasku narzędzi zawiera opcje **Moje rozwiązanie**, **bieżącego projektu**, i **bieżącego dokumentu**.

Po wybraniu podrzędny element członkowski w **hierarchii wywołań** okienka widoku drzewa:

- **Hierarchii wywołań** okienku szczegółów zostaną wyświetlone wszystkie wiersze kodu, w którym ten podrzędny element członkowski jest wywoływana z nadrzędnego elementu członkowskiego.

- **Definicji kodu** okna, jeśli otwarty, zawiera kod dla wybranego elementu członkowskiego (tylko C++). Aby uzyskać więcej informacji dotyczących tego okna, zobacz [wyświetlanie struktury kodu](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> **Hierarchii wywołań** funkcji nie znaleźć metody odwołania do grup, w tym miejscach, gdzie metoda jest dodawana jako program obsługi zdarzeń lub jest przypisany do delegata. Aby znaleźć wszystkie odwołania do metody, można użyć **Znajdź wszystkie odwołania** polecenia.

## <a name="shortcut-menu-items"></a>Elementy menu skrótów

W poniższej tabeli opisano kilka opcji menu skrótów, które są dostępne po kliknięciu prawym przyciskiem myszy węzeł w okienku widoku drzewa.

|W Menu kontekstowym|Opis|
|-----------------------|-----------------|
|**Dodaj jako nowy element główny**|Dodaje wybrany węzeł w okienku widoku drzewa, jako nowego węzła głównego. Dzięki temu można koncentrować w określonym poddrzewie.|
|**Usuwanie głównego**|Usuwa wybrany główny węzeł w okienku widoku drzewa. Ta opcja jest dostępna wyłącznie z węzła głównego.<br /><br /> Można również użyć **usunąć głównego** przycisku paska narzędzi, aby usunąć wybrany główny węzeł.|
|**Przejdź do definicji**|Uruchamia polecenie Przejdź do definicji dla wybranego węzła. Powoduje to przejście do oryginalnej definicji dla wywołania elementu członkowskiego lub definicji zmiennej.<br /><br /> Aby uruchomić polecenie Przejdź do definicji, możesz dwukrotnie kliknij wybrany węzeł lub naciśnij klawisz F12, dla wybranego węzła.|
|**Znajdź wszystkie odwołania**|Uruchamia polecenie Znajdź wszystkie odwołania dla wybranego węzła. Znajduje to wierszy kodu w projekcie tego odwołania klasy lub elementu członkowskiego.<br /><br /> SHIFT + F12 umożliwia również uruchomić polecenie Znajdź wszystkie odwołania dla wybranego węzła.|
|**Kopiuj**|Kopiuje zawartość wybranego węzła (ale nie jego węzłami podrzędnymi).|
|**Odśwież**|Zwija wybrany węzeł, aby ponownie rozszerzanie on Wyświetla bieżące informacje.|