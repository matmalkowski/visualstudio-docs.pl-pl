---
title: 'CA2228: Nie dostarczaj niepublikowanych formatów zasobów'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1928cb4626ea5d5af15ecf800a8842d66f3e244d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Nie dostarczaj niepublikowanych formatów zasobów
|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Plik zasobów został utworzony przy użyciu wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] który nie jest obecnie obsługiwany.

## <a name="rule-description"></a>Opis reguły
 Pliki zasobów, które zostały skompilowane przy użyciu wersji wstępnych [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nie może być używana przez obsługiwane wersje programu .NET Framework.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, tworzenie zasobu, używając obsługiwanej wersji programu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.