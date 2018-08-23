---
title: Właściwości definicji DSL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5c5ebb4672cdbb82692dc01339409ef7fa91c2d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42693996"
---
# <a name="properties-of-a-dsl-definition"></a>Właściwości definicji DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [właściwości definicji DSL](https://docs.microsoft.com/visualstudio/modeling/properties-of-a-dsl-definition).  
  
Zdefiniuj właściwości DslDefinition *języka specyficznego dla domeny* definicji właściwości, takie jak numerowanie wersji. Właściwości DslDefinition są wyświetlane w **właściwości** okno po kliknij pusty obszar na diagramie w *projektanta języka specyficznego dla domeny*.  
  
 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o tym, jak korzystać z tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 DslDefinition ma właściwości w poniższej tabeli:  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Modyfikator dostępu|Określa, czy modyfikator dostępu dla klasy domeny jest publiczny lub wewnętrzny.|public|  
|Atrybuty niestandardowe|Niestandardowe zdefiniowane atrybuty dla klasy domeny.<br /><br /> **Uwaga** używaj przycisku Przeglądaj, aby dodać atrybut.|\<Brak >|  
|Nazwa firmy|Nazwa bieżącej nazwy firmy w rejestrze systemowym.|Bieżąca nazwa firmy|  
|Nazwa|Nazwa tej klasy domeny.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw stowarzyszona z tą klasą domeny.|Bieżąca przestrzeń nazw|  
|Identyfikator Guid pakietu|Identyfikator guid dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pakietu wygenerowanego dla tego języka DSL.|\<Brak >|  
|Namespace pakietu|Przestrzeń nazw dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pakietu wygenerowanego dla tego języka DSL.|\<Brak >|  
|Nazwa produktu|Nazwa produktu, który ma zostać zarejestrowany dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pakietu wygenerowanego dla tego języka DSL.|\<Brak >|  
|Uwagi|Informacje o skojarzone z tą klasą domeny.|\<Brak >|  
|Opis|Opis dla tej klasy domeny.|\<Brak >|  
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej klasy domeny.|\<Brak >|  
|Słowo kluczowe pomocy|Słowo kluczowe Pomocy skojarzone z tą klasą domeny.|\<Brak >|  
|Kompilacja|Numer kompilacji przyrostowych dla tej definicji języka specyficznego dla domeny.|0|  
|Wersja główna|Numer kompilacji przyrostowej głównych dla tej definicji języka specyficznego dla domeny.|1|  
|Wersja pomocnicza|Numer kompilacji przyrostowej pomocniczej dla tej definicji języka specyficznego dla domeny.|0|  
|Poprawki|Przyrostowych wersji kompilacji numer dla tej definicji języka specyficznego dla domeny.|0|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzi języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



