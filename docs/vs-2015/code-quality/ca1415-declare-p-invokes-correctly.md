---
title: 'CA1415: P-Invoke poprawnie Zadeklaruj | Dokumentacja firmy Microsoft'
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
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8a3c6d338d916ed58a2279fc2848070b88e29d88
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628897"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Należy poprawnie zadeklarować P/Invokes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1415: zadeklarować P-Invoke poprawnie](https://docs.microsoft.com/visualstudio/code-quality/ca1415-declare-p-invokes-correctly).  
  
Element TypeName | DeclarePInvokesCorrectly |  
| CheckId | CA1415 |  
| Kategoria | Microsoft.Interoperability|  
| Zmiana powodująca niezgodność | Bez podziału — Jeśli P/Invoke, która deklaruje parametru nie są widoczne poza zestawem. Istotne — Jeśli P/Invoke, która deklaruje parametr są widoczne poza zestaw. |  
  
## <a name="cause"></a>Przyczyna  
 Metoda wywołania platformy nieprawidłowo zadeklarowano.  
  
## <a name="rule-description"></a>Opis reguły  
 Platforma wywołania metody uzyskuje dostęp do niezarządzanego kodu i jest definiowana za pomocą `Declare` — słowo kluczowe w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Obecnie ta reguła będzie wyglądać dla deklaracji metod, których platformą docelową funkcji Win32, które mają wskaźnikiem do parametru struktury OVERLAPPED wywołania platformy, a odpowiadający parametr zarządzalny nie jest wskaźnikiem do <xref:System.Threading.NativeOverlapped?displayProperty=fullName> struktury.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, należy poprawnie zadeklarować platformy wywołania metody.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano wywołanie platformy metody, które naruszają reguły i spełniać reguły.  
  
 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z kodem niezarządzanym](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



