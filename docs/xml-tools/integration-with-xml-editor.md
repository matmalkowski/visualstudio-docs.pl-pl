---
title: Projektant schematu XML integracji z edytora XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ae7595121fcefa36998a88b53aae466d3a726cb
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573326"
---
# <a name="integration-with-xml-editor"></a>Integracja z edytora XML

Projektant schematu XML jest zintegrowana z edytora XML. Jeśli zmodyfikujesz plik XSD w edytorze XML, zmiany zostaną odzwierciedlone w [Eksploratora schematu XML](../xml-tools/xml-schema-explorer.md). Jeśli masz [widok wykresu](../xml-tools/graph-view.md) lub [widoku modelu zawartości](../xml-tools/content-model-view.md) otwarty, zmiana będzie również tam widoczne. Można przechodzić między edytorze XML i Projektant schematu XML w następujący sposób:

-   W edytorze XML, kliknij prawym przyciskiem myszy węzeł i wybierz **Pokaż w Eksploratorze schematu XML**.

-   W widoku wykresu i **Eksploratora schematu XML**, kliknij dwukrotnie węzeł, lub kliknij prawym przyciskiem myszy węzeł i wybierz **kod widoku**. W widoku modelu zawartości, kliknij węzeł prawym przyciskiem myszy i wybierz **kod widoku**.

Poniższy zrzut ekranu przedstawia schematu XML otwarty w **Eksploratora schematu XML**. **Eksploratora schematu XML** Wyświetla schemat w widoku drzewa. Edytor XML Wyświetla widok tekstu węzła, który jest obecnie aktywny w **Eksploratora schematu XML**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

Czasami jest przydatne wyświetlić kod w edytorze XML i graficznego projektanta obok siebie. Aby wyświetlić oba pliki w tym samym czasie, kliknij prawym przyciskiem myszy w edytorze XML, a następnie wybierz **Widok projektanta**. Wybierz z menu programu Visual Studio Windows **nowe poziomy (lub pionową) grupy kart**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Zobacz także

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)