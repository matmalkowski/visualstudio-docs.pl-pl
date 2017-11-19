---
title: "Sprawdzanie poprawności kodu XML dokumentu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e6e4b91bb64601dbd54046e7d9a3ebfd9a73943
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="xml-document-validation"></a>Sprawdzanie poprawności kodu XML dokumentu
Edytor XML sprawdza składni XML 1.0 i również wykonuje sprawdzanie poprawności danych podczas pisania. Edytor można sprawdzić za pomocą definicji typu dokumentu (DTD) lub schematu. Czerwone faliste podkreślenie zaznacz wszystkie błędy poprawnie sformułowanym XML 1.0. Faliste podkreślenie niebieski Pokaż błędy semantyczne w oparciu DTD lub schemat sprawdzania poprawności. Każdy z błędów ma skojarzonego wpisu na liście błędów. Można również wyświetlić komunikat o błędzie przez umieszczenie wskaźnika myszy nad faliste podkreślenie.  
  
 Schematy użyte podczas weryfikowania znajdują się przez dopasowanie `targetNamespace` skompilowanych schematu z elementu deklaracji xmlns. Skompilowany schematy są załadowane z jednego z następujących lokalizacji, w kolejności priorytetu:  
  
-   Z nazwa pliku określona w **schematy** pola w oknie właściwości dokumentu.  
  
-   Wbudowany schemat lub definicji DTD.  
  
-   Zewnętrzna definicja DTD lub `xsd:schemaLocation` i `xsd:noNamespaceSchemaLocation` atrybutu  
  
-   "X-schema" XDR przestrzeń nazw schematu identyfikatora URI.  
  
Schematy można także znaleźć w następujących lokalizacjach dodatkowych, gdy schemat ma niepusty docelowego obszaru nazw:  
  
-   Inne okno edytora zawierający schematu.  
  
-   Schemat w bieżącym rozwiązaniu.  
  
-   Schemat z katalogu pamięci podręcznej schematu.  
  
## <a name="xslt-files"></a>Pliki XSLT  
 Podczas edytowania pliku XSLT, plik xslt.xsd, znajdujący się w pamięci podręcznej schematu służy do sprawdzania poprawności. Błędy sprawdzania poprawności są wyświetlane jako niebieskie faliste podkreślenie. Błędy kompilatora XSLT są wyświetlane jako czerwone faliste podkreślenie.  
  
## <a name="xml-schema-xsd-files"></a>Pliki XML Schema (XSD)  
 Edytując plik schematu XML, plik xsdschema.xsd, znajdujący się w pamięci podręcznej schematu służy do sprawdzania poprawności. Błędy sprawdzania poprawności są wyświetlane jako niebieskie faliste podkreślenie. Błędy kompilacji są także wyświetlane z czerwonym faliste podkreślenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)