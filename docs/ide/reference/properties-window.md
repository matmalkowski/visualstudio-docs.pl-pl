---
title: Okno Właściwości
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2848a8197dfe62836918de51ae6e7d01677dac6d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947303"
---
# <a name="properties-window"></a>Okno Właściwości
To okno dialogowe umożliwia wyświetlanie i zmiana właściwości czasu projektowania i zdarzenia wybranych obiektów, które znajdują się w edytorach i projektantów. Można również użyć **właściwości** okna do edycji i wyświetlanie plików projektu i właściwości rozwiązania. Można znaleźć **właściwości** okno na **widoku** menu. Możesz również otworzyć go, naciskając klawisz F4 lub wpisując **właściwości** w **Szybkie uruchamianie** okna.

 **Właściwości** okna przedstawia różne typy edytowania pola, w zależności od potrzeb danej właściwości. Te obszary edycji zawierają pola edycji, listy rozwijane i łącza do niestandardowego edytora okien dialogowych. Właściwości wyświetlane w kolorze szarym są tylko do odczytu.

## <a name="uielement-list"></a>Lista elementów UI
 Nazwa obiektu

 Wyświetla listę aktualnie zaznaczonego obiektu lub obiektów. Widoczne są tylko obiekty z active editor lub projektanta. Po wybraniu wielu obiektów są wyświetlane tylko właściwości wspólne dla wszystkich wybranych obiektów.

 Podzielone

 Wyświetla listę wszystkich właściwości i wartości właściwości dla wybranego obiektu według kategorii. Można zwinąć kategorię, aby zmniejszyć liczbę widocznych właściwości. Gdy rozwinąć lub zwinąć kategorię, zobacz znakiem plus (+) lub minus (-) z lewej strony nazwy kategorii. Kategorie są wymienione w kolejności alfabetycznej.

 Alfabetyczne

 Sortuje alfabetycznie wszystkie właściwości czasu projektowania i zdarzeń dla wybranych obiektów. Aby edytować właściwości normalnym kolorem, kliknij komórkę po jego prawej stronie, a następnie wprowadź zmiany.

 Strony właściwości

 Wyświetla **strony właściwości** okno dialogowe lub **projektanta projektu** dla wybranego elementu. Strony właściwości przedstawia podzbiór, w tym samym lub podzbiorem właściwości dostępne w **właściwości** okna. Ten przycisk służy do wyświetlania i edytowania właściwości związane z aktywną konfigurację projektu.

 Właściwości

 Wyświetla właściwości dla obiektu. Wiele obiektów również mieć zdarzenia, które można wyświetlić przy użyciu **właściwości** okna.

 Sortuj według źródła właściwości

 Właściwości grupy według źródła, takich jak dziedziczenia, stosowane style i powiązania. Dostępne tylko podczas edytowania plików XAML w projektancie.

 Zdarzenia

 Wyświetla zdarzenia dla obiekt.

> [!NOTE]
> To **właściwości** formantu paska narzędzi okna jest dostępna, gdy formularz tylko lub projektanta formantów jest aktywny w kontekście [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu. Podczas edytowania plików XAML, zdarzenia są wyświetlane na osobnej karcie okna właściwości.


 Komunikaty

 Wyświetla listę wszystkich komunikatów systemu Windows. Służy do dodawania i usuwania funkcji określony program obsługi komunikatów podany dla wybranej klasy.

> [!NOTE]
> To **właściwości** formantu paska narzędzi okna jest dostępna tylko podczas **widoku klasy** jest aktywnym oknem w kontekście [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu.


 Overrides

 Wyświetla listę wszystkich funkcji wirtualnych dla wybranej klasy i umożliwia dodawanie lub usuwanie zastępowanie funkcji.

> [!NOTE]
> To **właściwości** formantu paska narzędzi okna jest dostępna tylko podczas **widoku klasy** jest aktywnym oknem w kontekście [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu.


 Okienko opisu

 Pokazuje typ właściwości oraz krótki opis właściwości. Opis właściwości i Włącz w menu skrótów za pomocą polecenia opis można włączyć.

> [!NOTE]
> To **właściwości** formantu paska narzędzi okna nie jest dostępna podczas edytowania plików XAML w projektancie.


 Widok miniatur

 Pokazuje wizualną reprezentację aktualnie zaznaczonego elementu podczas edycji plików XAML w projektancie.

 Wyszukaj

 Udostępnia funkcję wyszukiwania dla właściwości i zdarzenia podczas edytowania plików XAML w projektancie. Pole wyszukiwania odpowiada do wyszukiwania wyrazów częściowe i aktualizacje wyniki wyszukiwania podczas wpisywania.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)