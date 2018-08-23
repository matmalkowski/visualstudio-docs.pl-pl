---
title: 'CA1901: Deklaracje P-Invoke powinny być przenośne | Dokumentacja firmy Microsoft'
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
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 685d576594a442f4cac510b5e29000ca0b6d3eb3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42691554"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Deklaracje P/Invoke powinny być przenośne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1901: deklaracje P-Invoke powinny być przenośne](https://docs.microsoft.com/visualstudio/code-quality/ca1901-p-invoke-declarations-should-be-portable).  
  
Element TypeName | PInvokeDeclarationsShouldBePortable |  
| CheckId | CA1901 |  
| Kategoria | Microsoft.Portability|  
| Zmiana powodująca niezgodność | Istotne - P/Invoke jest widoczna spoza zestawu. Bez podziału — Jeśli P/Invoke nie jest widoczna spoza zestawu. |  
  
## <a name="cause"></a>Przyczyna  
 Ta reguła oblicza rozmiar każdego parametru oraz wartość zwracaną metody P/Invoke i sprawdza, czy ich rozmiar przekazywania do kodu niezarządzanego na platformach 32-bitowych i 64-bitowych jest poprawny. Najbardziej typowe naruszenie tej zasady jest do przekazania liczby całkowitej stałych rozmiarach, w których wymagane jest zależny od platformy, wskaźnika wielkości zmiennej.  
  
## <a name="rule-description"></a>Opis reguły  
 Jedną z następujących scenariuszy narusza tę regułę występuje:  
  
-   Wartość zwracana lub parametr jest wpisane jako liczba całkowita stałym rozmiarze, gdy powinna być typizowana jako `IntPtr`.  
  
-   Wartość zwracana lub parametr jest wpisana jako `IntPtr` kiedy powinna być typizowana jako liczbą całkowitą o stałym rozmiarze.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 To naruszenie można rozwiązać za pomocą `IntPtr` lub `UIntPtr` do reprezentowania dojścia, zamiast `Int32` lub `UInt32`.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie należy pominąć to ostrzeżenie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano naruszenie tej zasady.  
  
```csharp  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 W tym przykładzie `nIconIndex` parametru jest zadeklarowany jako `IntPtr`, który wynosi 4 bajty szerokiego to platforma 32-bitowych i 8 bajtów szerokości na platformie 64-bitowej. W deklaracji niezarządzanych poniżej, możesz zobaczyć, że `nIconIndex` jest 4-bajtowa liczba całkowita bez znaku na wszystkich platformach.  
  
```csharp  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## <a name="example"></a>Przykład  
 Aby naprawić naruszenie, zmień deklarację do następujących:  
  
```csharp  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Ostrzeżenia dotyczące przenośności](../code-quality/portability-warnings.md)



