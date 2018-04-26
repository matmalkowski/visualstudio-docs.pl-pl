---
title: Właściwości dokumentu XML, okno właściwości
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4610a2574fbd822e4468436655668cff3892270
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="xml-document-properties-properties-window"></a>Właściwości dokumentu XML, okno właściwości

**Właściwości** okna zawiera podstawowe informacje o dokument, który jest aktywny w edytorze XML. Właściwości, które są dostępne różne w zależności od typu dokumentu XML, który jest obecnie aktywny.

> [!NOTE]
> Wszystkie właściwości dokumentu XML są zapisywane w rozwiązaniu. W związku z tym nie trzeba ponownie przy następnym otwarciu rozwiązania te wartości.

 **Kodowanie**

 Kodowanie znaków dla pliku. Zmienianie tej właściwości również zmiany kodowanie atrybutu deklaracji XML i odwrotnie. Nowe kodowanie będzie służyć do kodowania pliku podczas zapisywania pliku.

 **Dane wejściowe**

 Dokument wejściowy skojarzone z arkusza stylów XSLT. Jest on używany przez **dane wyjściowe ShowXSLT** polecenia. Dokument można wybrać przy użyciu Przeglądaj (**...** ) przycisku.

 Ta właściwość jest widoczny tylko wtedy, gdy plik XSLT jest aktualnie aktywne w oknie edytora.

 **Output**

 Plik, który jest generowany, gdy Przekształcanie dokumentu XML.

 Jeśli plik nie zostanie określony, domyślna nazwa pliku jest generowany na podstawie `method` atrybutu `xsl:output` element, który określa rozszerzenie pliku. Domyślny plik znajduje się w katalogu tymczasowym bieżącego użytkownika.

 **Schematy**

 Schematy do użycia w celu weryfikacji. Ten przycisk otwiera **schematów XSD** okno dialogowe, którego można użyć do wybrania schematy do użycia.

 Można również wprowadzić ścieżkę, aby schematów. Jeśli określonych jest wiele schematów, każda ścieżka schematu musi być ujęta w cudzysłów.

 **Arkusz stylów**

 Plik XSLT, który jest używany do transformacji dokumentów po **Pokaż dane wyjściowe XSLT** używane jest polecenie. Jeśli to pole jest puste, gdy **Pokaż dane wyjściowe XSLT** używane jest polecenie, Edytor korzysta z wartości w `xml-stylesheet` przetwarzania instrukcji dokument, lub wyświetla monit o podanie nazwy pliku.

 Podczas edytowania pliku XSLT, tej właściwości można określić różnych stylów należy używane podczas **Pokaż dane wyjściowe XSLT** lub **debugowania XSLT** polecenia jest zaznaczone. Na przykład możesz to zrobić, edytując arkusz stylów, który znajduje się w arkuszu stylów nadrzędnej.

## <a name="see-also"></a>Zobacz też

- [Edytor XML](../xml-tools/xml-editor.md)
- [Składniki edytora XML](../xml-tools/xml-editor-components.md)