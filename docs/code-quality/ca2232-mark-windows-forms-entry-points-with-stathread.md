---
title: "CA2232: Punkty wejścia formularzy systemu Windows znak za pomocą STAThread | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fe12ce5947a22414aaf07c59945fd667b106101f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Oznacz punkty wpisu formularzy systemu Windows za pomocą STAThread
|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Odwołuje się do zestawu <xref:System.Windows.Forms> przestrzeni nazw, a jego punktu wejścia nie jest oznaczony atrybutem <xref:System.STAThreadAttribute?displayProperty=fullName> atrybutu.  
  
## <a name="rule-description"></a>Opis reguły  
 <xref:System.STAThreadAttribute>Wskazuje jednowątkowego apartamentu COM wątkowość modelu dla aplikacji. Atrybut ten musi być obecny w punkcie wejścia każdej aplikacji korzystającej z Windows Forms; jeśli zostanie pominięty, składniki systemu Windows mogą nie działać poprawnie. Jeśli ten atrybut nie jest obecny, aplikacja używa modelu typu apartment wielowątkowe, który nie jest obsługiwana dla formularzy systemu Windows.  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]nie trzeba oznaczyć projektów, które używają struktury aplikacji **Main** metody za pomocą STAThread. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Kompilatora zrobi to automatycznie.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Dodaj <xref:System.STAThreadAttribute> atrybutu do punktu wejścia. Jeśli <xref:System.MTAThreadAttribute?displayProperty=fullName> obecny jest atrybut, usuń go.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Można bezpiecznie pominąć ostrzeżenie od tej reguły, jeśli tworzysz dla programu .NET Compact Framework, dla którego <xref:System.STAThreadAttribute> atrybut jest niepotrzebne i nie jest obsługiwany.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano prawidłowe użycie <xref:System.STAThreadAttribute>.  
  
 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]