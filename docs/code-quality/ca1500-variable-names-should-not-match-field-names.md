---
title: "CA1500: Nazwy zmiennych nie powinny odpowiadać nazwom pól | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7825078ff4d53ad5d90cdd8765f6f4120805b60f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Nazwy zmiennych nie powinny odpowiadać nazwom pól
|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|CheckId|CA1500|  
|Kategoria|Microsoft.Maintainability|  
|Zmiana kluczowa|Gdy jest uruchamiany na parametr, który ma taką samą nazwę jak pole:<br /><br /> Nierozdzielające — Jeśli pole i metody, która deklaruje parametru nie są widoczne spoza zestawu, niezależnie od tego, wprowadzone zmiany.<br />-Podziału — Jeśli zmiana nazwy pola i może być widoczny spoza zestawu.<br />-Przerywanie — Jeśli zmienisz nazwę parametru i metody, która deklaruje on widoczne poza zestaw.<br /><br /> Gdy uruchamiane w zmiennej lokalnej, która ma taką samą nazwę jak pole:<br /><br /> Nierozdzielające — Jeśli pole nie są widoczne spoza zestawu, niezależnie od tego, wprowadzone zmiany.<br />Nierozdzielające — Jeśli zmiana nazwy zmiennej lokalnej i nie należy zmieniać nazwy pola.<br />-Przerywanie — Jeśli zmieniasz nazwę pola i może być widoczny spoza zestawu.|  
  
## <a name="cause"></a>Przyczyna  
 Metody wystąpienia deklaruje parametr lub zmienna lokalna, którego nazwa odpowiada pole wystąpienia typu deklarującego. Aby catch zmienne lokalne, które naruszają zasady, przetestowany zestaw muszą zostać skompilowane przy użyciu informacji o debugowaniu i program skojarzony plik bazy danych (.pdb) muszą być dostępne.  
  
## <a name="rule-description"></a>Opis reguły  
 Gdy nazwa pola wystąpienia jest zgodna z parametrem lub nazwę zmiennej lokalnej, pole wystąpienia jest dostępny za pomocą `this` (`Me` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) — słowo kluczowe podczas wewnątrz treści metody. Utrzymywanie kodu, jest łatwe do zapomnisz tej różnicy i założono, że parametr/lokalnej zmiennej odwołuje się do pola wystąpienia, co prowadzi do błędów. Dotyczy to zwłaszcza treści metody długie.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Zmień nazwę parametru/zmiennej lub pola.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwa naruszenia reguły.  
  
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]