---
title: "CA1504: Przegląd mylących nazw pól | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dc1317380eab4a63a7c60557fbec258485768885
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Przegląd mylących nazw pól
|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|Kategoria|Microsoft.Maintainability|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa pola wystąpienia rozpoczyna się od "s_" lub nazwa `static` (`Shared` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) pola rozpoczyna się ciągiem "m_".  
  
## <a name="rule-description"></a>Opis reguły  
 Pole o nazwach zaczynających "s_" są skojarzone z danych statycznych przez wielu użytkowników. Podobnie nazwami pola, które zaczynają się ciągiem "m_" są skojarzone z danych wystąpienia (członek). Dla zapewnienia łatwiej kodu nazw powinna zgodne z konwencjami powszechnie używanych.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Zmień nazwę pola, używając odpowiedniego prefiksu. Można również określić pole Akceptuję bieżącego sufiks przez dodanie lub usunięcie `static` modyfikator.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.