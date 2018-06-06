---
title: Sprawdzanie poprawności dokumentu XML w edytorze XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04b2e821abbbc7a24ce5b77b7374de617852cf2a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693841"
---
# <a name="xml-document-validation"></a>Sprawdzanie poprawności kodu XML dokumentu

Edytor XML sprawdza składni XML 1.0 i również wykonuje sprawdzanie poprawności danych podczas pisania. Edytor można sprawdzić za pomocą definicji typu dokumentu (DTD) lub schematu. Czerwone faliste podkreślenie zaznacz wszystkie błędy poprawnie sformułowanym XML 1.0. Faliste podkreślenie niebieski Pokaż błędy semantyczne w oparciu DTD lub schemat sprawdzania poprawności. Każdy z błędów ma skojarzonego wpisu na liście błędów. Można również wyświetlić komunikat o błędzie przez umieszczenie wskaźnika myszy nad faliste podkreślenie.

 Schematy użyte podczas weryfikowania znajdują się przez dopasowanie `targetNamespace` skompilowanych schematu z elementu deklaracji xmlns. Skompilowany schematy są załadowane z jednego z następujących lokalizacji, w kolejności priorytetu:

-   Z nazwa pliku określona w **schematy** pole dokumentu **właściwości** okna.

-   Wbudowany schemat lub definicji DTD.

-   Zewnętrzna definicja DTD lub `xsd:schemaLocation` i `xsd:noNamespaceSchemaLocation` atrybutu

-   "X-schema" XDR przestrzeń nazw schematu identyfikatora URI.

Schematy można także znaleźć w następujących lokalizacjach dodatkowych, gdy schemat ma niepusty docelowego obszaru nazw:

-   Inne okno edytora zawierający schematu.

-   Schemat w bieżącym rozwiązaniu.

-   Schemat z katalogu pamięci podręcznej schematu.

## <a name="xslt-files"></a>Pliki XSLT
 Podczas edytowania pliku XSLT *xslt.xsd* plik znajdujący się w pamięci podręcznej schematu jest używany do sprawdzania poprawności. Błędy sprawdzania poprawności są wyświetlane jako niebieskie faliste podkreślenie. Błędy kompilatora XSLT są wyświetlane jako czerwone faliste podkreślenie.

## <a name="xml-schema-xsd-files"></a>Pliki XML schema (XSD)
 Podczas edytowania pliku schematu XML *xsdschema.xsd* plik znajdujący się w pamięci podręcznej schematu jest używany do sprawdzania poprawności. Błędy sprawdzania poprawności są wyświetlane jako niebieskie faliste podkreślenie. Błędy kompilacji są także wyświetlane z czerwonym faliste podkreślenie.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)