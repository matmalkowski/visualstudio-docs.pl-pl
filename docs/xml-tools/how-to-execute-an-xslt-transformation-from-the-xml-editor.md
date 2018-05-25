---
title: 'Porady: wykonywanie transformację XSLT w edytorze XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 892f82d64bb022c20c786a996bf9f89cf557b4c2
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Porady: wykonywanie transformację XSLT w edytorze XML

Edytor XML umożliwia skojarzenie arkusz stylów XSLT z dokumentu XML na przekształcenie i wyświetlić dane wyjściowe. Dane wyjściowe z przekształcenia XSLT, który jest wyświetlany w nowym oknie dokumentu.

**Dane wyjściowe** właściwość określa nazwę pliku dla danych wyjściowych. Jeśli **dane wyjściowe** właściwość jest pusta, nazwa pliku jest generowany w katalogu tymczasowym. Rozszerzenie pliku jest oparta na `xsl:output` element swojego stylu arkusza i może być. *XML*,. *txt* lub. *htm*.

Jeśli **dane wyjściowe** właściwość określa nazwę pliku. *htm* lub. *HTML* rozszerzenia, dane wyjściowe XSLT jest przeglądanego przy użyciu [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] programu Internet Explorer. Wszystkie inne rozszerzenia plików otwartych przy użyciu wybranego przez domyślny edytor [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] programu Visual Studio. Na przykład, jeśli rozszerzenie pliku. *xml*, Visual Studio będzie korzystać z edytora XML.

## <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Do wykonania transformację XSLT z dokumentu XML

1.  Otwórz dokument XML w edytorze XML.

2.  Arkusz stylów XSLT skojarzony z dokumentem XML.

    -   Dodaj `xml-stylesheet` przetwarzania instrukcji do dokumentu XML. Na przykład, Dodaj następujący wiersz `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` do prologu dokumentu.

         —lub—

    -   Dodawanie using arkusz stylów XSLT **właściwości** okna. W dokumencie **okna właściwości**, kliknij przycisk **Przeglądaj** przycisk dla **arkusza stylów** , wybierz arkusz stylów XSLT, a następnie kliknij przycisk **Otwórz**.

3.  Kliknij przycisk **dane wyjściowe ShowXSL** znajdującego się na **edytora XML** paska narzędzi.

    > [!NOTE]
    > Jeśli nie ma żadnych arkusza stylów powiązany z dokumentem XML, okno dialogowe wyświetli monit o Podaj arkusza stylów do użycia.
    >
    >  Dane wyjściowe z przekształcenia XSLT, który jest wyświetlany w nowym oknie dokumentu.

## <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Do wykonania transformację XSLT z arkusz stylów XSLT

1.  Otwórz arkusz stylów XSLT w edytorze XML.

2.  Określ dokument XML w **dane wejściowe** pole dokumentu **właściwości** okna.

    > [!NOTE]
    > Dokument XML jest używany do transformacji dokument wejściowy. Jeśli nie określono dokumentu, gdy przekształcenie XSLT jest uruchomiona, **Otwórz plik** zostanie wyświetlone okno dialogowe, a w tym czasie można określić dokumentu.

3.  Kliknij przycisk **dane wyjściowe ShowXSLT** znajdującego się na **edytora XML** paska narzędzi.

     Dane wyjściowe z przekształcenia XSLT, który jest wyświetlany w nowym oknie dokumentu.

## <a name="to-provide-a-different-output-file-name"></a>Aby podać nazwę pliku wyjściowego różnych

1.  Określ nazwę pliku w **dane wyjściowe** pole dokumentu **właściwości** okna.

2.  Kliknij przycisk **dane wyjściowe ShowXSLT** znajdującego się na **edytora XML** paska narzędzi.

     Dane wyjściowe z przekształcenia XSLT, który jest wyświetlany w nowym oknie dokumentu i rozszerzenie pliku zależy od edytora używane w oknie danych wyjściowych z **dane wyjściowe** właściwości dokumentu.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)