---
title: Wyświetl parametry w Wizualizator ciągu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/11/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3a0575b02422bf83dd560d3eae5724b0a50d3f3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476978"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Wyświetl parametry w ciągu wizualizatora w Visual Studio
Podczas debugowania, możesz otworzyć wizualizatora ciąg do widoku ciągów, które są zbyt długie, aby wyświetlić w oknie danych porady lub debugera. W wielu scenariuszach Wizualizator może pomóc zidentyfikować ciągi nieprawidłowo sformułowany.

Standardowy ciąg wbudowanych wizualizatorów obejmują zwykłego tekstu, XML, HTML i JSON. Dla kilku innych typów, takich jak obiekty WPF, które pojawiają się w debugerze, takich jak windows **automatycznych** okna, można również otworzyć wizualizatorów.

## <a name="open-a-string-visualizer"></a>Otwórz Wizualizator ciągu

Aby wyświetlić zwykłego tekstu, ciąg XML, HTML lub JSON, kliknij ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ikona wizualizatora") podczas kursora myszy nad zmiennej zawierającej wartość ciągu. Użytkownik musi być wstrzymane w debugerze umożliwiające wyświetlanie ikonę lupy.

![Otwórz Wizualizator ciągu](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>Widok danych dotyczących ciągu

**Wyrażenie** pole w Wizualizator ciągu zawiera bieżąca zmienna lub wyrażenie aktywowany przez debuger.

**Wartość** pole zawiera wartość ciągu. Wizualizator tekst zawiera zwykły tekst.

Pusty **wartość** wskazuje, że określone wizualizatora nie można rozpoznać typu ciąg. Na przykład wizualizatora XML zawiera pusty **wartość** na ciąg w formacie ciągu zwykłego tekstu (z żadnych znaczników XML) lub JSON. Aby wyświetlić nierozpoznawalną ciągu w wizualizatora, należy użyć narzędzia text visualizer.

### <a name="view-json-string-data"></a>Widok danych dotyczących ciągu JSON

Poprawnie sformułowany ciąg JSON zostaną wyświetlone informacje podobne do poniższej ilustracji w wizualizatora JSON. Ikona błędu (lub pusty w przypadku nierozpoznany) mogą być wyświetlane nieprawidłowo sformatowany kod JSON.

![Wizualizator ciągu JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Wizualizator ciągu JSON")

### <a name="view-xml-string-data"></a>Widok danych dotyczących ciągu XML

Poprawnie sformułowany ciąg XML pojawi się podobnie jak na poniższej ilustracji w wizualizatora XML. Bez tagów XML (lub pusty w przypadku nierozpoznany) mogą być wyświetlane nieprawidłowo sformułowany kod XML.

![Wizualizator ciągu XML](../debugger/media/dbg-string-visualizers-xml.png "Wizualizator ciągu XML")

### <a name="view-html-string-data"></a>Widok HTML danych dotyczących ciągu

Poprawnie sformułowany ciąg HTML jest podobny do widoku, które można zobaczyć Jeśli ciąg jest renderowany w przeglądarce, jak pokazano na poniższej ilustracji. Nieprawidłowo sformułowany HTML może być wyświetlany jako zwykły tekst.

![Wizualizator ciągu HTML](../debugger/media/dbg-string-visualizers-html.png "Wizualizator ciągu HTML")

## <a name="see-also"></a>Zobacz też  
 [Utwórz niestandardowe Wizualizatory (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)