---
title: "Właściwości relacji domeny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3f81f4bca6d268cd9fd32a6edf44cbde40d7c357
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="properties-of-domain-relationships"></a>Właściwości relacji domeny
Właściwości w poniższej tabeli są skojarzone z relacji domeny. Informacje o relacje domeny, zobacz [opis modeli, klasy i relacje](../modeling/understanding-models-classes-and-relationships.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Modyfikator dostępu|Poziom dostępu relacji domeny (`public` lub `internal`).|`public`|  
|Atrybuty niestandardowe|Można dodać atrybuty do klasy kodu źródłowego, które są generowane na podstawie relacji domeny.|\<Brak >|  
|Generuje o podwójnej precyzji pochodnych|Jeśli `True`, generowany jest zarówno klasy podstawowej i częściowej klasy (obsługuje dostosowywania przy użyciu zastąpień). Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Ma niestandardowy konstruktora|Jeśli `True`, wskazuje, czy niestandardowy konstruktor podano w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowany na podstawie relacji domeny (`none`, `abstract` lub `sealed`).|\<Brak >|  
|Umożliwia duplikatów|Jeśli `True`, można tworzyć łącza zduplikowanych relacji domeny między tym samym dwa elementy.|`False`|  
|Relacje podstawowe|Jeśli pochodzi relacji domeny, relacji podstawowych relacji domeny.|\<Brak >|  
|Jest osadzanie|Jeśli `True`, relacji domeny jest relacja osadzania. Jeśli `False`, relacja jest relacją odwołania.|\<zarówno >|  
|Nazwa|Nazwa relacji domeny.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona z relacji domeny.|Bieżącej przestrzeni nazw|  
|Uwagi|Nieformalne uwagi, które są skojarzone z relacji domeny.|\<Brak >|  
|Opis|Opis, który jest używany do kod dokumentów i jest używany w Interfejsie użytkownika wygenerowanego projektanta.|\<Brak >|  
|Nazwa wyświetlana|Nazwa, która jest wyświetlana w Projektancie wygenerowany dla relacji domeny.|\<Brak >|  
|Słowo kluczowe pomocy|Optional-słowo kluczowe służący do indeksu Pomocy F1 dla relacji domeny.|\<Brak >|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)