---
title: "Właściwości definicji DSL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 793d4becea65caca5bf127707c96c44de028fd3d
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="properties-of-a-dsl-definition"></a>Właściwości definicji DSL
Definiowanie właściwości DslDefinition *języka specyficznego dla domeny* definicji właściwości, takie jak numerów wersji. Właściwości DslDefinition są wyświetlane w **właściwości** okna po kliknięciu Otwórz obszar wykresu w *projektanta języka specyficznego dla domeny*.  
  
 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 DslDefinition ma właściwości w poniższej tabeli:  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Modyfikator dostępu|Określa, czy modyfikator dostępu dla klasy domeny jest publiczny lub wewnętrzny.|public|  
|Atrybuty niestandardowe|Niestandardowe zdefiniowane przez atrybuty dla klasy domeny.<br /><br /> **Uwaga** użyj przycisku przeglądania, aby dodać atrybut.|\<none>|  
|Nazwa firmy|Nazwa bieżącego nazwę firmy w rejestrze systemu.|Bieżąca nazwa firmy|  
|Nazwa|Nazwa klasy tej domeny.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw powiązane z tą klasą domeny.|Bieżącej przestrzeni nazw|  
|Identyfikator Guid pakietu|Identyfikator guid [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pakietu wygenerowany dla tej DSL.|\<none>|  
|Namespace pakietu|W obszarze nazw [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pakietu wygenerowany dla tej DSL.|\<none>|  
|Nazwa produktu|Nazwa produktu, który zostanie zarejestrowany dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pakietu wygenerowany dla tej DSL.|\<none>|  
|Uwagi|Notatki skojarzone z tą klasą domeny.|\<none>|  
|Opis|Opis dla tej klasy domeny.|\<none>|  
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w Projektancie wygenerowany dla tej klasy domeny.|\<none>|  
|Słowo kluczowe pomocy|Słowo kluczowe Pomocy skojarzone z tą klasą domeny.|\<none>|  
|Kompilacja|Numer kompilacji przyrostowej dla tej definicji języka specyficznego dla domeny.|0|  
|Wersja główna|Numer kompilacji przyrostowej głównych dla tej definicji języka specyficznego dla domeny.|1|  
|Wersja pomocnicza|Numer kompilacji przyrostowej pomocnicze dla tej definicji języka specyficznego dla domeny.|0|  
|Poprawki|Przyrostowych wersji kompilacji dla definicji tego języka specyficznego dla domeny.|0|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)