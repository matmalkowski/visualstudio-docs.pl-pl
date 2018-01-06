---
title: "Porady: edytowanie plików XML | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8720fe94797e212cb332368572b291ce7fb40a26
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-edit-xml-files"></a>Porady: edytowanie plików XML
Edytor XML jest nowy edytora plików XML. Może służyć autonomiczny plik XML lub pliku skojarzone z projektu programu Visual Studio. Edytor XML jest skojarzony z następujących rozszerzeń: .config, .dtd .xml, XSD, .xdr, XSL, .xslt i .vssettings. Edytor XML jest także powiązany z innego typu pliku mający nie Edytor zarejestrowany i zawiera zawartość XML lub definicji DTD.  
  
> [!NOTE]
>  XHTML dokumentów są obsługiwane przez edytor HTML.  
  
### <a name="to-edit-an-xml-file"></a>Aby edytować plik XML  
  
1.  Kliknij dwukrotnie plik, który chcesz edytować.  
  
### <a name="to-add-a-new-xml-file-to-a-project"></a>Aby dodać nowy plik XML do projektu  
  
1.  Z **projektu** menu, wybierz opcję **Dodaj nowy element**.  
  
2.  Wybierz **pliku XML** z **szablony** okienka.  
  
3.  Wprowadź nazwę pliku w **nazwa** pole i naciśnij klawisz **Dodaj**.  
  
     Plik XML jest dodawane do projektu i otwarty w edytorze XML. Plik zawiera deklarację XML domyślne `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### <a name="to-add-an-existing-xml-file-to-a-project"></a>Aby dodać istniejący plik XML do projektu  
  
1.  Z **projektu** menu, wybierz opcję **Dodaj istniejący element**.  
  
     **Dodaj istniejący element** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz plik XML i naciśnij klawisz **Dodaj**.  
  
### <a name="to-create-a-new-xml-or-xslt-file"></a>Aby utworzyć nowy plik XML lub XSLT  
  
1.  Z **pliku** menu, wybierz opcję **nowy**.  
  
     **Nowy plik** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz **pliku XML** można utworzyć nowego pliku XML; lub wybierz **pliku XSLT** do utworzenia nowego arkusza stylów XSLT.  
  
3.  Kliknij przycisk **Otwórz**.  
  
### <a name="to-create-a-project-for-xml-files"></a>Aby utworzyć projekt dla plików XML  
  
1.  Z **pliku** menu, wybierz opcję **nowy**, a następnie wybierz **projektu**.  
  
     **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz język kodu wybranych przez użytkownika, wybierz opcję **pusty projekt**i kliknij przycisk **OK**.  
  
3.  Dodaj pliki XML do projektu.  
  
     Edytor XML znajduje schematów, które dodasz do tego projektu i używa ich do walidacji i IntelliSense w dowolnym XML, schemat lub pliki XSLT, które można edytować, gdy ten projekt jest otwarty.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)   
 [Właściwości dokumentu XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md)   
 [Instrukcje: Tworzenie schematu XML z dokumentu XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)