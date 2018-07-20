---
title: Wyświetl parametry w wizualizatorze ciąg | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ca6e4519a85659b36e5cf6baebaadd1d1c626f1a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151038"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Wyświetl parametry w wizualizatorze ciągów w programie Visual Studio
Podczas debugowania, możesz otworzyć wizualizatora ciąg znaków do ciągów widoku, które są zbyt długie, aby wyświetlić w oknie danych porady lub debugera. W wielu scenariuszach wizualizatora pomaga zidentyfikować ciągi źle sformułowane.

Wizualizatory standardowego ciągu wbudowanych obejmują zwykły tekst, XML, HTML i JSON. Dla kilku innych typów, takich jak WPF obiekty, które są wyświetlane w debugerze systemu windows, takich jak **Autos** okna, można również otworzyć wizualizatorów.

## <a name="open-a-string-visualizer"></a>Otwórz Wizualizator ciągu

Aby wyświetlić zwykłego tekstu, XML, HTML lub JSON ciąg, kliknij na ikonę szkła powiększającego ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ikonę Wizualizator") podczas najeżdżania kursorem na zmienną zawierającą wartość ciągu. Musi być został wstrzymany w debugerze umożliwiające wyświetlanie ikonę lupy.

![Otwórz Wizualizator ciągu](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>Wyświetl dane ciągu

**Wyrażenie** pola w wizualizatorze ciąg przedstawia bieżącej zmiennej lub wyrażenia najechania kursorem w debugerze.

**Wartość** pole zawiera wartość ciągu. Wizualizator tekstu zawiera zwykły tekst.

Blank **wartość** wskazuje, że określone visualizer nie może rozpoznać typu string. Na przykład Wizualizator XML pokazuje pusty **wartość** dla ciąg w formacie ciągu zwykłego tekstu (z nie znaczników XML) lub JSON. Jeśli zachodzi potrzeba wyświetlenia nierozpoznawalną ciągu w wizualizatorze, korzystanie z wizualizatora tekstu.

### <a name="view-json-string-data"></a>Wyświetl dane ciągu JSON

Poprawnie sformułowany ciąg JSON pojawi się podobnie jak na poniższej ilustracji w wizualizatorze JSON. Ikona błędu (lub pusty w przypadku nierozpoznany) mogą być wyświetlane nieprawidłowo sformatowany kod JSON. Jeśli widoczna jest ikona błędu, skopiuj i Wklej ciąg JSON do narzędzia Zaznaczanie błędów JSON, takich jak [JSLint](https://www.jslint.com/) do identyfikowania błąd danych JSON.

![Wizualizator ciągu JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Wizualizator ciągu JSON")

### <a name="view-xml-string-data"></a>Wyświetl dane ciągu XML

Pojawi się podobnie jak na poniższej ilustracji w wizualizatorze XML sformułowany ciąg XML. Nieprawidłowo sformułowany kod XML mogą być wyświetlane bez znaczników XML (lub pusty w przypadku nierozpoznany).

![Wizualizator ciągu XML](../debugger/media/dbg-string-visualizers-xml.png "Wizualizator ciągu XML")

### <a name="view-html-string-data"></a>Dane ciągu widok HTML

Poprawnie sformułowany ciąg HTML jest podobny do widoku, zobaczysz czy jeśli ciąg jest wyświetlana w przeglądarce, jak pokazano na poniższej ilustracji. Źle sformułowane HTML może być wyświetlany jako zwykły tekst.

![Wizualizator ciągu HTML](../debugger/media/dbg-string-visualizers-html.png "Wizualizator ciągu HTML")

## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowych Wizualizatorów (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)