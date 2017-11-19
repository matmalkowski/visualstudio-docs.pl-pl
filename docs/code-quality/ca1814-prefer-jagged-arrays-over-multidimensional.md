---
title: 'CA1814: Wybieraj Tablice nieregularne zamiast wielowymiarowych | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa1420ab01426cbfeaaf5d70238df19fde50ea9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Wybieraj tablice nieregularne zamiast wielowymiarowych
|||  
|-|-|  
|TypeName|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Element członkowski jest zadeklarowany jako tablicy wielowymiarowej.  
  
## <a name="rule-description"></a>Opis reguły  
 Nieregularna tablica to ta, której elementy są tablicami. Tablice, które tworzą elementy, mogą mieć różne rozmiary, co zapewnia większą oszczędność miejsca w przypadku niektórych zestawów danych.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, zmień tablicy wielowymiarowej na tablicy nieregularnej.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomiń ostrzeżenie od tej reguły, jeśli tablica wielowymiarowa nie są używane do miejsca.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono zgłoszeń Tablice nieregularne i wielowymiarowych.  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]