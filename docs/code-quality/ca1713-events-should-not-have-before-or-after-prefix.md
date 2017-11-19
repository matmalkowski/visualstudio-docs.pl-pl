---
title: "CA1713: Zdarzenia nie powinny mieć, prefiksów before ani after | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c211d2f2cc65c12fd11782058c5e8b8a3aaf47b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713 Zdarzenia nie powinny posiadać prefiksów Before ani After
|||  
|-|-|  
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa zdarzenia rozpoczyna się od "Przed" i "After".  
  
## <a name="rule-description"></a>Opis reguły  
 Nazwy zdarzenia powinny opisują akcję, która wywołuje zdarzenie. Nazwa powiązanych zdarzeń, które są wywoływane w określonej kolejności, używa czasu teraźniejszego lub przeszłego, aby wskazać względne położenie akcji w sekwencji. Na przykład gdy nazewnictwa para zdarzeń, które jest wywoływane podczas zamykania zasobu, może być nazwy "Zamykanie" i "Closed" zamiast "BeforeClose" i "AfterClose".  
  
 Konwencje nazewnictwa Podaj wygląd wspólnej dla bibliotek przeznaczonych środowisko uruchomieniowe języka wspólnego. Zmniejsza to nauki jest wymagany dla nowej biblioteki oprogramowania, którą można tworzyć bardziej niezawodne klienta, czy biblioteka został opracowany przez osobę, która ma doświadczenia w rozwijającym się kodu zarządzanego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Usuń prefiks z nazwy zdarzenia i Rozważ zmianę nazwy obecnie lub przeszłego zlecenia.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.