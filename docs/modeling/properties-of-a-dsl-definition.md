---
title: "Właściwości definicji DSL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: "13"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 7a8fc0474f624785a47a4ba9f970b5a1ca54dd9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-a-dsl-definition"></a>Właściwości definicji DSL
Definiowanie właściwości DslDefinition *języka specyficznego dla domeny* definicji właściwości, takie jak numerów wersji. Właściwości DslDefinition są wyświetlane w **właściwości** okna po kliknięciu Otwórz obszar wykresu w *projektanta języka specyficznego dla domeny*.  
  
 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 DslDefinition ma właściwości w poniższej tabeli:  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Modyfikator dostępu|Określa, czy modyfikator dostępu dla klasy domeny jest publiczny lub wewnętrzny.|public|  
|Atrybuty niestandardowe|Niestandardowe zdefiniowane przez atrybuty dla klasy domeny.<br /><br /> **Uwaga** użyj przycisku przeglądania, aby dodać atrybut.|\<Brak >|  
|Nazwa firmy|Nazwa bieżącego nazwę firmy w rejestrze systemu.|Bieżąca nazwa firmy|  
|Nazwa|Nazwa klasy tej domeny.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw powiązane z tą klasą domeny.|Bieżącej przestrzeni nazw|  
|Identyfikator Guid pakietu|Identyfikator guid [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pakietu wygenerowany dla tej DSL.|\<Brak >|  
|Namespace pakietu|W obszarze nazw [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pakietu wygenerowany dla tej DSL.|\<Brak >|  
|Nazwa produktu|Nazwa produktu, który zostanie zarejestrowany dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pakietu wygenerowany dla tej DSL.|\<Brak >|  
|Uwagi|Notatki skojarzone z tą klasą domeny.|\<Brak >|  
|Opis|Opis dla tej klasy domeny.|\<Brak >|  
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w Projektancie wygenerowany dla tej klasy domeny.|\<Brak >|  
|Słowo kluczowe pomocy|Słowo kluczowe Pomocy skojarzone z tą klasą domeny.|\<Brak >|  
|Kompilacja|Numer kompilacji przyrostowej dla tej definicji języka specyficznego dla domeny.|0|  
|Wersja główna|Numer kompilacji przyrostowej głównych dla tej definicji języka specyficznego dla domeny.|1|  
|Wersja pomocnicza|Numer kompilacji przyrostowej pomocnicze dla tej definicji języka specyficznego dla domeny.|0|  
|Poprawki|Przyrostowych wersji kompilacji dla definicji tego języka specyficznego dla domeny.|0|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)