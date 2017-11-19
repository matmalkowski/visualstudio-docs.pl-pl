---
title: "Pojęcia dotyczące programu MSBuild | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
caps.latest.revision: "13"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 4395f4c82be689b1d573be44948e98711ba066c3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-concepts"></a>Pojęcia dotyczące programu MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]udostępnia podstawowe schematu XML, który służy do kontrolowania sposobu platformy kompilacji Kompilacje oprogramowania. Aby określić składniki w kompilacji i sposób ich ma zostać utworzony, użyj programu MSBuild tych czterech części: właściwości, elementy, zadań i elementów docelowych.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Właściwości programu MSBuild](../msbuild/msbuild-properties.md)|Wprowadza właściwości i kolekcji właściwości. Właściwości są pary klucz wartość, których można użyć do skonfigurowania kompilacji.|  
|[Elementy](../msbuild/msbuild-items.md)|W tym artykule opisano ogólne pojęcia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] plik formatu i sposób elementy dopasowania.|  
|[Obiekty docelowe](../msbuild/msbuild-targets.md)|Wyjaśniono, jak grupy zadań w określonej kolejności i Włącz sekcje proces kompilacji ma być wywoływana w wierszu polecenia.|  
|[Zadania](../msbuild/msbuild-tasks.md)|Pokazuje, jak utworzyć jednostkę kodu wykonywalnego, który może być używany przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do wykonywania operacji niepodzielnych kompilacji.|  
|[Porównanie właściwości i elementów](../msbuild/comparing-properties-and-items.md)|Porównanie właściwości programu MSBuild i elementów. Oba są używane do przekazywania informacji do zadania, Oszacuj warunki i przechowywać wartości, które można odwoływać się w pliku projektu.|  
|[Znaki specjalne w programie MSBuild](../msbuild/msbuild-special-characters.md)|Wyjaśniono, jak zmienić znaczenie niektórych znaków, które [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rezerwuje użytku specjalne w określonym kontekście.|  
|[Wskazówki: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Przedstawiono sposób tworzenia pliku podstawowego projektu przyrostowo, używając tylko tekstowy edytora.|  
|[Wskazówki: Korzystanie z MSBuild](../msbuild/walkthrough-using-msbuild.md)|Wprowadza blokami konstrukcyjnymi elementów MSBuild oraz sposób zapisu, manipulowanie nimi oraz debugowania projektów MSBuild bez zamykania programu Visual Studio zintegrowane środowisko programistyczne (IDE).|  
|[Odwołanie do MSBuild](../msbuild/msbuild-reference.md)|Linki do dokumentów, które zawierają informacje o odwołaniu.|  
|[MSBuild](../msbuild/msbuild.md)|Zawiera omówienie schematu XML w pliku projektu i pokazuje, jak kontroluje procesów, które Kompilacje oprogramowania.|