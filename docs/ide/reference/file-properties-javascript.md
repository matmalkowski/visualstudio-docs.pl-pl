---
title: Właściwości pliku, JavaScript
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.expandedsdknode.fileversion
- javascript.project.property.expandedsdknode.uri
- javascript.project.property.expandedsdknode.filename
- javascript.project.property.reference.description
- javascript.project.property.reference.specificversion
- javascript.project.property.reference.identity
- javascript.project.property.fullpath
- javascript.project.property.packageaction
- javascript.project.property.reference.package
- javascript.project.property.copytooutputdirectory
- javascript.project.property.expandedsdknode.sdkpath
- javascript.project.property.reference.filetype
- javascript.project.property.reference.culture
- javascript.project.property.filename
- javascript.project.property.reference.resolvedpath
- javascript.project.property.reference.version
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db9809c48b9226e05b7617c860af524b1ac6daf6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="file-properties-javascript"></a>Właściwości pliku, JavaScript
Wskaż, jakie akcje system projektu należy wykonać na plikach, można użyć właściwości pliku. Na przykład można ustawić właściwości pliku, aby wskazać, czy plik powinien być dodany do pakietu jako plik zasobów.

 Można wybrać dowolny plik w Eksploratorze rozwiązań i sprawdź jej właściwości w oknie właściwości. Pliki JavaScript ma cztery właściwości: **Kopiuj do katalogu wyjściowego**, **Akcja opakowaniu**, **nazwę pliku**, i **ścieżka pliku**.

## <a name="file-properties"></a>Właściwości pliku
 W tej sekcji opisano właściwości wspólne dla plików JavaScript.

### <a name="copy-to-output-directory-property"></a>Kopiuj do właściwości katalogu wyjściowego
 Ta właściwość określa warunki, w których plik wybranego źródła zostanie skopiowany do katalogu wyjściowego. Wybierz **nie należy kopiować** Jeśli plik nie ma zostać skopiowany do katalogu wyjściowego. Wybierz **skopiuj zawsze** Jeśli plik jest zawsze ma zostać skopiowany do katalogu wyjściowego. Wybierz **Kopiuj, jeśli nowszy** Jeśli plik jest do skopiowania tylko wtedy, gdy jest nowsza niż istniejący plik o tej samej nazwie w katalogu wyjściowego.

### <a name="package-action"></a>Akcja pakietu
 **Akcja opakowaniu** właściwość wskazuje co program Visual Studio nie przy użyciu pliku podczas wykonywania kompilacji. **Czynność dotycząca pakietów** może mieć jeden z kilku wartości:

-   **Brak** — plik nie jest dołączony do manifestu pakietu. Przykład to plik tekstowy, który zawiera dokumentację, takich jak plik Readme.

-   **Zawartości** — plik jest dołączony do manifestu pakietu. Na przykład to ustawienie jest wartością domyślną dla htm, js, CSS, obrazów, plików audio i wideo.

-   **Manifest** — plik nie jest dołączony do manifestu pakietu. Zamiast tego pliku jest używany dla danych wejściowych podczas generowania manifestu pakietu. Jest to wartość domyślna dla pliku package.appxmanifest.

-   **Zasób** — plik nie jest dołączony do manifestu pakietu. Zamiast tego zawartość pliku są indeksowane w indeksu zasobów pakietu (PRI), który jest przesyłany do manifestu pakietu. Zwykle służy do plików zasobów.

Wartość domyślna dla **Akcja opakowaniu** zależy od rozszerzenie pliku, który można dodać do rozwiązania.

### <a name="file-name-property"></a>Właściwość nazwy pliku
 Wyświetla nazwę pliku jako wartość tylko do odczytu. Aby zmienić nazwę pliku, należy kliknąć prawym przyciskiem myszy w Eksploratorze rozwiązań i wybrać **zmienić**.

### <a name="full-path-property"></a>Pełna ścieżka właściwości
 Wyświetla pełną ścieżkę do pliku jako wartość tylko do odczytu. Aby zmienić ścieżkę do pliku, możesz przeciągania i upuszczania plików w Eksploratorze rozwiązań.

## <a name="reference-file-properties"></a>Odwołanie do właściwości pliku
 W tej sekcji opisano właściwości wspólne dla plików odwołanie z aplikacji platformy uniwersalnej systemu Windows, utworzony przy użyciu języka JavaScript. Po wybraniu odwołania, takich jak plik winmd, odwołanie do zestawu SDK, odwołanie projektu do projektu lub odwołania do zestawu w Eksploratorze rozwiązań innych właściwości mogą być wyświetlane w oknie właściwości zgodnie z typem pliku.

### <a name="culture"></a>Kultury
 Wyświetla język skojarzony z odwołania.

### <a name="file-type"></a>Typ pliku
 Wyświetla typ pliku odwołania.

### <a name="file-version"></a>Wersja pliku
 Wyświetla wersję pliku odwołania.

### <a name="identity"></a>Tożsamość
 Wyświetla tożsamość odwołania, który jest używany w projekcie, który jest przechowywany w pliku projektu.

### <a name="package"></a>Package
 Wyświetla nazwę skojarzonej z odwołaniem manifestu pakietu.

### <a name="resolved-path"></a>Rozpoznana ścieżka
 Wyświetla ścieżkę odwołania, który jest używany w projekcie.

### <a name="sdk-path"></a>Ścieżka zestawu SDK
 Wyświetla ścieżkę do pliku odwołania zestawu SDK.

### <a name="uri"></a>Identyfikator URI
 Wyświetla identyfikator URI, który musi być uwzględniona w HTML lub JavaScript pliki projektu do załączenia pliku jako pliku źródłowego.

### <a name="version"></a>Wersja
 Wyświetla wersję odwołania.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie właściwościami projektu i rozwiązania](../../ide/managing-project-and-solution-properties.md)