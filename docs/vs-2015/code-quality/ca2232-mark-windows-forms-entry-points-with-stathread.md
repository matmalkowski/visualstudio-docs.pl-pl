---
title: 'CA2232: Punkty wejścia formularzy Windows znacznik za pomocą atrybutu STAThread | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5b7c479856ceddbf6785833d207984c9d01343e5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42627655"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Oznacz punkty wpisu formularzy systemu Windows za pomocą STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2232: formularze Windows Oznacz punkty wejścia za pomocą atrybutu STAThread](https://docs.microsoft.com/visualstudio/code-quality/ca2232-mark-windows-forms-entry-points-with-stathread).  
  
Element TypeName | MarkWindowsFormsEntryPointsWithStaThread |  
| CheckId | CA2232 |  
| Kategoria | Microsoft.Usage|  
| Zmiana powodująca niezgodność | Inne niż powodująca niezgodność |  
  
## <a name="cause"></a>Przyczyna  
 Odwołuje się zestaw <xref:System.Windows.Forms> przestrzeni nazw i jego punktu wejścia nie jest oznaczony atrybutem <xref:System.STAThreadAttribute?displayProperty=fullName> atrybutu.  
  
## <a name="rule-description"></a>Opis reguły  
 <xref:System.STAThreadAttribute> Wskazuje, że model wątkowości COM dla aplikacji jest jednowątkowym apartamentem. Atrybut ten musi być obecny w punkcie wejścia każdej aplikacji korzystającej z Windows Forms; jeśli zostanie pominięty, składniki systemu Windows mogą nie działać poprawnie. Jeśli ten atrybut nie jest obecny, aplikacja korzysta z modelu apartamentu wielowątkowych, który nie jest obsługiwana dla formularzy Windows Forms.  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nie trzeba oznaczyć projektów używających struktury aplikacji **Main** metody za pomocą atrybutu STAThread. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Kompilatora zrobi to automatycznie.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, należy dodać <xref:System.STAThreadAttribute> atrybutu do punktu wejścia. Jeśli <xref:System.MTAThreadAttribute?displayProperty=fullName> atrybut był obecny, usuń ją.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomijaj ostrzeżeń dla tej reguły, jeśli tworzysz dla platformy .NET Compact Framework, dla którego można bezpiecznie <xref:System.STAThreadAttribute> atrybut jest niepotrzebne i nie jest obsługiwana.  
  
## <a name="example"></a>Przykład  
 Poniższe przykłady pokazują poprawne użycie <xref:System.STAThreadAttribute>.  
  
 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]



