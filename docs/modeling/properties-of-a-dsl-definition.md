---
title: Właściwości definicji DSL
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: be119703868316f2335f06174c9f21c2dddd2edc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949595"
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

- [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)