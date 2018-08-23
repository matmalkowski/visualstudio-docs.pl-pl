---
title: 'CA2124: Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try | Dokumentacja firmy Microsoft'
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
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c486c4a6469e1c20b48a953f04201f1dba586d04
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628146"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Kodowanie wrażliwych klauzul finally w zewnętrznym try
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2124: Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try](https://docs.microsoft.com/visualstudio/code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try).  
  
Element TypeName | WrapVulnerableFinallyClausesInOuterTry |  
| CheckId | CA2124 |  
| Kategoria | Microsoft.Security|  
| Zmiana powodująca niezgodność | Inne niż powodująca niezgodność |  
  
## <a name="cause"></a>Przyczyna  
 W wersjach 1.0 i 1.1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], metoda publiczna lub chroniona zawiera `try` / `catch` / `finally` bloku. `finally` Bloku pojawia się, aby zresetować stan zabezpieczeń i nie jest ujęty w `finally` bloku.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta zasada lokalizuje `try` / `finally` bloki w kodzie, który jest przeznaczony dla wersji 1.0 i 1.1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , mogą być narażone na filtry wyjątków złośliwego obecne w stosie wywołań. Jeśli poufnych operacje, takie jak personifikacji występują w bloku try, zgłaszany jest wyjątek, filtr, można wykonać przed `finally` bloku. Na przykład personifikacji oznacza to, że filtr jest wykonywany jako nazwa spersonifikowanego użytkownika. Filtry są obecnie implementable tylko w języku Visual Basic.  
  
> [!WARNING]
>  **Uwaga** w wersji 2.0 lub nowszej [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], środowisko wykonawcze automatycznie chroni `try` / `catch` /  `finally` uniemożliwiaj filtry wyjątków złośliwy, jeśli wystąpi resetowania bezpośrednio w metodzie, która zawiera bloku wyjątków.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Umieść nieopakowane `try` / `finally` w zewnętrzny blok try. Zobacz drugim przykładzie poniżej. Zmusza to `finally` do wykonania przed uruchomieniem kodu filtru.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod  
  
### <a name="description"></a>Opis  
 Poniższy pseudo-kod przedstawiono wzorzec wykryte przez tę regułę.  
  
### <a name="code"></a>Kod  
  
```  
try {  
   // Do some work.  
   Impersonator imp = new Impersonator("John Doe");  
   imp.AddToCreditCardBalance(100);  
}  
finally {  
   // Reset security state.  
   imp.Revert();  
}  
```  
  
## <a name="example"></a>Przykład  
 Pseudo-poniższy kod przedstawia wzorzec służące do ochrony kodu i spełniają tej reguły.  
  
```  
try {  
     try {  
        // Do some work.  
     }  
     finally {  
        // Reset security state.  
     }  
}  
catch()  
{  
    throw;  
}  
```



