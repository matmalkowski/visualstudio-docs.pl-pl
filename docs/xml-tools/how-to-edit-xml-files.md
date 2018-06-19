---
title: 'Porady: edytowanie plików XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3754bcf87d77a3a67801ef7f9df8e07dc687b052
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549132"
---
# <a name="how-to-edit-xml-files"></a>Porady: edytowanie plików XML

Edytor XML jest nowy edytora plików XML. Może służyć autonomiczny plik XML lub pliku skojarzone z projektu programu Visual Studio. Edytor XML jest skojarzony z następujących rozszerzeń: *.config*, *.dtd*, *.xml*, *XSD*, *.xdr*, *.xsl*, *.xslt*, i *.vssettings*. Edytor XML jest także powiązany z innego typu pliku mający nie Edytor zarejestrowany i zawiera zawartość XML lub definicji DTD.

> [!NOTE]
> XHTML dokumentów są obsługiwane przez edytor HTML.

## <a name="to-edit-an-xml-file"></a>Aby edytować plik XML

1.  Kliknij dwukrotnie plik, który chcesz edytować.

### <a name="to-add-a-new-xml-file-to-a-project"></a>Aby dodać nowy plik XML do projektu

1.  Z **projektu** menu, wybierz opcję **Dodaj nowy element**.

2.  Wybierz **pliku XML** z **szablony** okienka.

3.  Wprowadź nazwę pliku w **nazwa** pole i naciśnij klawisz **Dodaj**.

     Plik XML jest dodawane do projektu i otwarty w edytorze XML. Plik zawiera deklarację XML domyślne `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="to-add-an-existing-xml-file-to-a-project"></a>Aby dodać istniejący plik XML do projektu

1.  Z **projektu** menu, wybierz opcję **Dodaj istniejący element**.

     **Dodaj istniejący element** zostanie wyświetlone okno dialogowe.

2.  Wybierz plik XML i naciśnij klawisz **Dodaj**.

## <a name="to-create-a-new-xml-or-xslt-file"></a>Aby utworzyć nowy plik XML lub XSLT

1.  Z **pliku** menu, wybierz opcję **nowy**.

     **Nowy plik** zostanie wyświetlone okno dialogowe.

2.  Wybierz **pliku XML** można utworzyć nowego pliku XML; lub wybierz **pliku XSLT** do utworzenia nowego arkusza stylów XSLT.

3.  Kliknij przycisk **Otwórz**.

## <a name="to-create-a-project-for-xml-files"></a>Aby utworzyć projekt dla plików XML

1.  Z **pliku** menu, wybierz opcję **nowy**, a następnie wybierz **projektu**.

     **Nowy projekt** zostanie wyświetlone okno dialogowe.

2.  Wybierz język kodu wybranych przez użytkownika, wybierz opcję **pusty projekt**i kliknij przycisk **OK**.

3.  Dodaj pliki XML do projektu.

     Edytor XML znajduje schematów, które dodasz do tego projektu i używa ich do walidacji i IntelliSense w dowolnym XML, schemat lub pliki XSLT, które można edytować, gdy ten projekt jest otwarty.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)
- [Właściwości dokumentu XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md)
- [Porady: tworzenie schematu XML z dokumentu XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)