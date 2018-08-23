---
title: Właściwości diagramów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 43d5804f1a80b2616e209c47e594b29ad84911a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677948"
---
# <a name="properties-of-diagrams"></a>Właściwości diagramów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [właściwości diagramów](https://docs.microsoft.com/visualstudio/modeling/properties-of-diagrams).  
  
Można ustawić właściwości, które określają, jak diagramy będzie wyświetlana w wygenerowanym projektancie. Na przykład można określić domyślny kolor tekstu na diagramie.  
  
 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o tym, jak korzystać z tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Poniższa tabela zawiera listę właściwości diagramów.  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Kolor wypełnienia|Kolor wypełnienia dla diagramu.|Biały|  
|Kolor tekstu|Kolor tekstu, która jest wyświetlana na diagramie.|Czarny|  
|Modyfikator dostępu|Modyfikator dostępu dla klasy (wewnętrznego lub publicznego).|Public|  
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy wygenerowanego kodu.|\<Brak >|  
|Generuje Double pochodne|Jeśli `True`, zostaną wygenerowane klasy podstawowej i klasy częściowej (obsługuje dostosowywania przy użyciu zastąpień). Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ma konstruktora niestandardowego|Jeśli `True`, konstruktora niestandardowego, które będą dostępne w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Modyfikator dziedziczenia|Opisuje typ dziedziczenia klasy kodu źródłowego, która jest generowany na podstawie diagramu (`none`, `abstract` lub `sealed`).|Brak|  
|Podstawowy Diagram|Klasa bazowa ten diagram.|(Brak)|  
|Nazwa|Nazwa tego diagramu.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona z tym diagramie.|Bieżąca przestrzeń nazw|  
|Reprezentowana klasa|Klasa domeny katalogu głównego ten diagram przedstawia.|Bieżąca klasa głównego, jeśli ma to zastosowanie|  
|Uwagi|Uwagi informacyjne, które są skojarzone z tym elementem.|\<Brak >|  
|Kolor wypełnienia ujawnia jako właściwość|Jeśli `True`, użytkownik może ustawić kolor wypełnienia diagram wygenerowanego projektanta. Aby to ustawić, kliknij prawym przyciskiem myszy kształt diagramu, a następnie kliknij przycisk **Dodaj Explosed**.|False|  
|Opisuje kolor tekstu jako właściwość|Jeśli `True`, użytkownik może ustawić kolor tekstu diagramu w wygenerowanym projektancie. Aby to ustawić, kliknij prawym przyciskiem myszy kształt diagramu, a następnie kliknij przycisk **Dodaj Explosed**.|False|  
|Opis|Opis, który jest używany do dokumentu wygenerowanego projektanta.|\<Brak >|  
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tego diagramu.|\<Brak >|  
|Słowo kluczowe pomocy|Słowo kluczowe, które jest używane do indeksowania pomocy F1 dla okna ten diagram.|\<Brak >|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzi języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



