---
title: 'Porady: tworzenie schematu XML z dokumentu XML | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b19421bf9cb9d974a837f557d8b75ac4d5ba89c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Porady: tworzenie schematu XML z dokumentu XML
Edytor XML umożliwia tworzenie schematu schematu XML definition language (XSD) z dokumentu XML. Dokument XML wystąpienia określa, jak schemat jest generowany w następujący sposób:  
  
-   Jeśli dokument XML nie ma żadnych schematu lub definicji typu dokumentu (DTD) skojarzonych z nim, dane w dokumencie XML służy do uwzględnienia nowego schematu XML.  
  
-   Jeśli dokument XML zawiera skojarzone DTD oraz zewnętrznej definicji DTD podzestawu wewnętrznego są konwertowane na odpowiedni schemat XML.  
  
-   Jeśli dokument XML zawiera wbudowanego schematu XML danych (XDR), schematu XDR jest konwertowana na odpowiedni schemat XML.  
  
Schematów, które są tworzone są następnie używane w celu zapewnienia IntelliSense dla dokumentu XML.  
  
Aby uzyskać więcej informacji na temat aparatu wnioskowania schematu, zobacz [wnioskowanie schematu XML](/dotnet/standard/data/xml/inferring-an-xml-schema).  
  
### <a name="to-create-an-xml-schema"></a>Aby utworzyć schematu XML  
  
1.  Załaduj dokument wystąpienia XML w edytorze XML.  
  
2.  Kliknij przycisk **Create Schema** przycisk z **narzędzi**.  
  
     Dokument schematu XML jest utworzony i otwarty dla każdej przestrzeni nazw w dokumencie wystąpienia XML. Każdy schematu jest otwarty jako plik tymczasowy dodatkowych.  
  
     Schematy może zapisano na dysku, dodane do projektu lub odrzucone.  
  
    > [!NOTE]
    >  **Create Schema** polecenia jest również dostępny w menu skrótów edytora XML i w obszarze **XML** menu.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)