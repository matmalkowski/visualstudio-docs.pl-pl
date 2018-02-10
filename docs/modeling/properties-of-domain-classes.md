---
title: "Właściwości klasy domeny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain class
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: b858aaea48643ead5ffca5c089c6c6f370f67835
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-domain-classes"></a>Właściwości klas domeny
Klasy domeny mają właściwości w poniższej tabeli. Aby uzyskać informacje o klasach domeny, zobacz [opis modeli, klasy i relacje](../modeling/understanding-models-classes-and-relationships.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Modyfikator dostępu|Poziom dostępu klasy domeny (`public` lub `internal`).|`public`|  
|Atrybuty niestandardowe|Można dodawać atrybuty do klasy kodu źródłowego, która jest generowana z tej klasy domeny.|\<none>|  
|Generuje o podwójnej precyzji pochodnych|Jeśli `True`, zarówno klasy podstawowej i częściowej klasy (obsługuje dostosowywania przy użyciu zastąpień) zostanie wygenerowany. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Ma niestandardowy konstruktora|Jeśli `True`, niestandardowe konstruktora znajdzie się w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana z klasy domeny (`none`, `abstract` lub `sealed`).|`none`|  
|Klasa podstawowa|Jeśli pochodzi ta klasa domeny, nazwę klasy podstawowej.|\<none>|  
|Nazwa|Nazwa klasy tej domeny.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw, klasy tej domeny.|Bieżącej przestrzeni nazw|  
|Uwagi|Nieformalne uwagi, które są skojarzone z tą klasą domeny.|\<none>|  
|Opis|Opis, który służy do interfejsu użytkownika projektanta wygenerowanego dokumentu.|\<none>|  
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w Projektancie wygenerowany dla tej klasy domeny.|\<none>|  
|Słowo kluczowe pomocy|Optional-słowo kluczowe służący do indeksu Pomocy F1 dla tej klasy domeny.|\<none>|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)