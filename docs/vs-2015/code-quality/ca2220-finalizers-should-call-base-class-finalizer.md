---
title: 'CA2220: Finalizatory powinny wywoływać finalizatory klasy bazowej | Dokumentacja firmy Microsoft'
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
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d9d116b8321694ae63ed3bfec6490c6c98b389c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680025"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizatory powinny wywoływać finalizatory klasy bazowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2220: finalizatory powinny wywoływać finalizatory klasy bazowej](https://docs.microsoft.com/visualstudio/code-quality/ca2220-finalizers-should-call-base-class-finalizer).  
  
Element TypeName | FinalizersShouldCallBaseClassFinalizer |  
| CheckId | CA2220 |  
| Kategoria | Microsoft.Usage|  
| Zmiana powodująca niezgodność | Inne niż powodująca niezgodność |  
  
## <a name="cause"></a>Przyczyna  
 Typ, który zastępuje <xref:System.Object.Finalize%2A?displayProperty=fullName> nie mogą wywoływać <xref:System.Object.Finalize%2A> metody w klasie bazowej.  
  
## <a name="rule-description"></a>Opis reguły  
 Finalizacja musi być powielana w hierarchii dziedziczenia. Aby to zapewnić, typy muszą wywołać klasy bazowej <xref:System.Object.Finalize%2A> metodę z własnych <xref:System.Object.Finalize%2A> metody. Kompilator języka C#, które automatycznie dodaje wywołanie finalizatory klasy bazowej.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, należy wywołać typ podstawowy <xref:System.Object.Finalize%2A> metody z Twojej <xref:System.Object.Finalize%2A> metody.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Niektóre kompilatory, których platformą docelową środowiska uruchomieniowego języka wspólnego Wstawianie wywołania finalizator typu podstawowego języka Microsoft intermediate language (MSIL). Jeśli ostrzeżenie od tej reguły jest zgłaszany, kompilator nie wstawić wywołanie i należy go dodać do kodu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie w języku Visual Basic przedstawiono typu `TypeB` poprawnie wywołująca <xref:System.Object.Finalize%2A> metody w klasie bazowej.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorzec Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



