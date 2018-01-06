---
title: "CA1901: Deklaracje P Invoke powinny być przenośne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6e0d3ce3d0130b0a2cf40f6d4f1716c32ae7c40e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Deklaracje P/Invoke powinny być przenośne
|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|Kategoria|Microsoft.Portability|  
|Zmiana kluczowa|Dzielenie - P/Invoke jest widoczna poza zestaw. Bez podziału — Jeśli P/Invoke nie jest widoczna poza zestaw.|  
  
## <a name="cause"></a>Przyczyna  
 Ta zasada oblicza rozmiar każdego parametru i wartość zwracaną P/Invoke i sprawdza, czy ich rozmiar przekazywane do kodu niezarządzanego na platformach 32-bitowe i 64-bitowych, jest poprawny. Najbardziej typowe naruszenie tej reguły jest do przekazania liczby całkowitej stałym rozmiarze, gdy wymagane jest zależny od platformy, wielkości wskaźnika zmiennej.  
  
## <a name="rule-description"></a>Opis reguły  
 Jedną z poniższych scenariuszy narusza tę regułę występuje:  
  
-   Zwracana wartość lub parametr jest typu jako liczba całkowita stałym rozmiarze, gdy należy wpisać jako `IntPtr`.  
  
-   Zwracana wartość lub parametr jest typu `IntPtr` po powinny być typizowane jako liczba całkowita stałym rozmiarze.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 To naruszenie można rozwiązać przy użyciu `IntPtr` lub `UIntPtr` do reprezentowania uchwytów zamiast `Int32` lub `UInt32`.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie należy pominąć to ostrzeżenie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano naruszenie tej reguły.  
  
```csharp  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 W tym przykładzie `nIconIndex` parametru jest zadeklarowany jako `IntPtr`, które wynosi 4 bajty szerokości na 32-bitowej platformy i 8 bajtów szerokości na 64-bitowej platformy. W deklaracji niezarządzane poniżej, można stwierdzić, że `nIconIndex` jest liczbą całkowitą bez znaku 4-bajtowych na wszystkich platformach.  
  
```csharp  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## <a name="example"></a>Przykład  
 Aby naprawić naruszenie, zmień deklarację do następującego:  
  
```csharp  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Ostrzeżenia dotyczące przenośności](../code-quality/portability-warnings.md)