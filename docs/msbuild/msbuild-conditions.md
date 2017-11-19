---
title: Warunki MSBuild | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
caps.latest.revision: "14"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: f3e4590a2623d05b78f4c62e877b0ff3783ceec9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-conditions"></a>Warunki MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]obsługuje określony zbiór warunków, które mogą być stosowane wszędzie tam, gdzie `Condition` atrybut jest dozwolony. W poniższej tabeli przedstawiono te warunki.  
  
|Warunek|Opis|  
|---------------|-----------------|  
|'`stringA`' == '`stringB`'|Daje w wyniku `true` Jeśli `stringA` jest równe `stringB`.<br /><br /> Na przykład:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Apostrofy nie są wymagane dla ciągów znaków alfanumerycznych prostego lub wartości typu boolean. Jednak apostrofy są wymagane dla wartości puste.|  
|'`stringA`' != '`stringB`'|Daje w wyniku `true` Jeśli `stringA` nie jest równa `stringB`.<br /><br /> Na przykład:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Apostrofy nie są wymagane dla ciągów znaków alfanumerycznych prostego lub wartości typu boolean. Jednak apostrofy są wymagane dla wartości puste.|  
|\<, >, \<=, >=|Oblicza wartości liczbowych argumenty operacji. Zwraca `true` Jeśli relacyjne ocena ma wartość true. Argumenty operacji musi być liczbą dziesiętną lub szesnastkową. Szesnastkowe musi rozpoczynać się od "0 x". **Uwaga:** w formacie XML, znaki `<` i `>` należy użyć znaków ucieczki. Symbol `<` jest reprezentowany jako `<`. Symbol `>` jest reprezentowany jako `>`.|  
|Istnieje ("`stringA`")|Daje w wyniku `true` Jeśli plik lub folder o nazwie `stringA` istnieje.<br /><br /> Na przykład:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Apostrofy nie są wymagane dla ciągów znaków alfanumerycznych prostego lub wartości typu boolean. Jednak apostrofy są wymagane dla wartości puste.|  
|HasTrailingSlash ("`stringA`")|Daje w wyniku `true` czy podany ciąg zawiera albo z poprzednimi wersjami ukośnika (\\) lub przesyłane znaku ukośnika (/).<br /><br /> Na przykład:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Apostrofy nie są wymagane dla ciągów znaków alfanumerycznych prostego lub wartości typu boolean. Jednak apostrofy są wymagane dla wartości puste.|  
|!|Daje w wyniku `true` , gdy argument jest `false`.|  
|I|Daje w wyniku `true` Jeśli oba operatory zwracają `true`.|  
|Lub|Daje w wyniku `true` , gdy co najmniej jeden z argumentów jest `true`.|  
|()|Grupowanie mechanizm, który daje w wyniku `true` Jeśli wynikiem obliczania wyrażenia znajdująca się wewnątrz `true`.|  
|$if$ (% wyrażenie %) $else$, $endif$|Sprawdza, czy określony `%expression%` jest zgodna z wartością ciągu parametru przekazany szablonu niestandardowego. Jeśli `$if$` warunek nie jest `true`, a następnie jego instrukcje są wykonywania; w przeciwnym razie `$else$` warunku jest zaznaczony. Jeśli `$else$` warunek jest `true`, a następnie jego instrukcje są wykonywania; w przeciwnym razie `$endif$` warunku kończy się Obliczanie wyrażenia.<br /><br /> Przykłady użycia można znaleźć [logiki parametru szablonu projektu/elementu programu Visual Studio](http://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md)   
 [Wskazówki: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)