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
ms.openlocfilehash: 7b2e2b7a9e6511faaa1941d65f6b328a07b10f79
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="integration-with-xml-editor"></a>Integracja z edytora XML

Projektant schematu XML jest zintegrowana z edytora XML. Jeśli zmodyfikujesz plik XSD w edytorze XML, zmiany zostaną odzwierciedlone w [Eksploratora schematu XML](../xml-tools/xml-schema-explorer.md). Jeśli masz [widok wykresu](../xml-tools/graph-view.md) lub [widoku modelu zawartości](../xml-tools/content-model-view.md) otwarty, zmiana będzie również tam widoczne. Można przechodzić między edytorze XML i Projektant schematu XML w następujący sposób:

-   W edytorze XML, kliknij prawym przyciskiem myszy węzeł i wybierz **Pokaż w Eksploratorze schematu XML**.

-   W widoku wykresu i Eksploratora schematu XML, kliknij dwukrotnie węzeł, lub kliknij prawym przyciskiem myszy węzeł i wybierz polecenie **kod widoku**. W widoku modelu zawartości, kliknij węzeł prawym przyciskiem myszy i wybierz **kod widoku**.

Poniższy zrzut ekranu przedstawia otworzyć schematu XML w Eksploratorze schematu XML. Eksploratora schematu XML zawiera schemat w widoku drzewa. Edytor XML przedstawia widok tekstu węzła, który jest obecnie aktywny w Eksploratorze schematu XML.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

Czasami jest przydatne wyświetlić kod w edytorze XML i graficznego projektanta obok siebie. Aby wyświetlić oba pliki w tym samym czasie, kliknij prawym przyciskiem myszy w edytorze XML, a następnie wybierz **Widok projektanta**. Wybierz z menu programu Visual Studio Windows **nowe poziomy (lub pionową) grupy kart**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Zobacz też

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)