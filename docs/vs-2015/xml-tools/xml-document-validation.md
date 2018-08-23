---
title: Walidacja dokumentów XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 990aceabc2fa5fa38ea6902eec9de39da7cb9eff
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42688615"
---
# <a name="xml-document-validation"></a>Walidacja dokumentów XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Walidacja dokumentów XML](https://docs.microsoft.com/visualstudio/xml-tools/xml-document-validation).  
  
  
Edytor XML sprawdza składni XML 1.0 i wykonuje sprawdzanie poprawności danych podczas wpisywania. Edytor może sprawdzić przy użyciu definicji typu dokumentu (DTD) lub schematu. Czerwone faliste podkreślenia Podświetl błędy sformułowany XML 1.0. Niebieskie faliste podkreślenia Pokaż błędy semantyczne w oparciu o DTD lub schematu sprawdzania poprawności. Każdy z błędów ma skojarzony wpis na liście błędów. Można również wyświetlić komunikat o błędzie, przez umieszczenie wskaźnika myszy nad falistą linią.  
  
 Schematy używane podczas sprawdzania poprawności znajdują się przez dopasowanie `targetNamespace` skompilowanych schematu z deklaracją xmlns elementu. Skompilowany schematy są załadowane z jednej z następujących lokalizacji, w kolejności priorytetu:  
  
-   Z pliku o nazwie określonej w **schematów** pola w oknie właściwości dokumentu.  
  
-   Wbudowany schemat lub DTD.  
  
-   Zewnętrznej definicji DTD lub `xsd:schemaLocation` i `xsd:noNamespaceSchemaLocation` atrybutu  
  
-   "X-schema" XDR schematu identyfikatora URI obszaru nazw.  
  
 Schematy można także znaleźć w następujących lokalizacjach dodatkowych, jeśli schemat zawiera pusty docelowego obszaru nazw:  
  
-   Inne okno edytora, która zawiera schemat.  
  
-   Schemat w bieżącym rozwiązaniu.  
  
-   Schemat z katalogu pamięci podręcznej schematu.  
  
## <a name="xslt-files"></a>Pliki XSLT  
 Podczas edytowania pliku XSLT, plik xslt.xsd, znajdujący się w pamięci podręcznej schematów służy do sprawdzania poprawności. Błędy sprawdzania poprawności są wyświetlane jako niebieskie faliste podkreślenia. Błędy kompilatora XSLT są wyświetlane jako czerwone faliste podkreślenia.  
  
## <a name="xml-schema-xsd-files"></a>Pliki schematów (XSD) XML  
 Edytując plik schematu XML, plik xsdschema.xsd, znajdujący się w pamięci podręcznej schematów służy do sprawdzania poprawności. Błędy sprawdzania poprawności są wyświetlane jako niebieskie faliste podkreślenia. Błędy kompilacji są także wyświetlane czerwoną, falistą.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)



