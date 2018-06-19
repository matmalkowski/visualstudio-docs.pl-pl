---
title: 'Porady: tworzenie schematu XML z dokumentu XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f33fc5b48b9fd6b1cc08570e62e73f05fd19e70
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548304"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Porady: tworzenie schematu XML z dokumentu XML

Edytor XML umożliwia tworzenie schematu schematu XML definition language (XSD) z dokumentu XML. Dokument XML wystąpienia określa, jak schemat jest generowany w następujący sposób:

-   Jeśli dokument XML nie ma żadnych schematu lub definicji typu dokumentu (DTD) skojarzonych z nim, dane w dokumencie XML służy do uwzględnienia nowego schematu XML.

-   Jeśli dokument XML zawiera skojarzone DTD oraz zewnętrznej definicji DTD podzestawu wewnętrznego są konwertowane na odpowiedni schemat XML.

-   Jeśli dokument XML zawiera wbudowanego schematu XML danych (XDR), schematu XDR jest konwertowana na odpowiedni schemat XML.

Schematów, które są tworzone są następnie używane w celu zapewnienia IntelliSense dla dokumentu XML.

Aby uzyskać więcej informacji na temat aparatu wnioskowania schematu, zobacz [wnioskowanie schematu XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Aby utworzyć schematu XML

1.  Załaduj dokument wystąpienia XML w edytorze XML.

2.  Kliknij przycisk **Create Schema** przycisk z **narzędzi**.

     Dokument schematu XML jest utworzony i otwarty dla każdej przestrzeni nazw w dokumencie wystąpienia XML. Każdy schematu jest otwarty jako plik tymczasowy dodatkowych.

     Schematy może zapisano na dysku, dodane do projektu lub odrzucone.

    > [!NOTE]
    >  **Create Schema** polecenia jest również dostępny w menu skrótów edytora XML i w obszarze **XML** menu.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)