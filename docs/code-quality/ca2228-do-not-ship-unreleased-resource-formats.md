---
title: "CA2228: Nie dostarczaj niepublikowanych formatów zasobów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 959d88751ff250e54f6a3f89f0b4b0554add96d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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