---
title: 'CA5350: Nie używaj słabych algorytmów kryptograficznych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 484b20a9c1d20cb0f18290de2277aa3feef26a8e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nie używaj słabych algorytmów kryptograficznych
|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|CheckId|CA5350|  
|Kategoria|Microsoft.Cryptography|  
|Zmiana kluczowa|Bez podziału|  
  
> [!NOTE]
>  To ostrzeżenie Data ostatniej aktualizacji listopada 2015 r.  
  
## <a name="cause"></a>Przyczyna  
 Algorytmy szyfrowania, takich jak <xref:System.Security.Cryptography.TripleDES> i tworzenia skrótów algorytmów, takich jak <xref:System.Security.Cryptography.SHA1> i <xref:System.Security.Cryptography.RIPEMD160> są uważane za słabe.  
  
 Te algorytmy kryptograficzne nie udostępniają tyle gwarancje bezpieczeństwa, jak nowoczesną odpowiedniki. Tworzenie skrótów algorytmów kryptograficznych <xref:System.Security.Cryptography.SHA1> i <xref:System.Security.Cryptography.RIPEMD160> zapewniają odporność mniej kolizji niż nowoczesną algorytmami wyznaczania wartości skrótu. Algorytm szyfrowania <xref:System.Security.Cryptography.TripleDES> zawiera mniej bity zabezpieczeń niż nowoczesną algorytmów szyfrowania.  
  
## <a name="rule-description"></a>Opis reguły  
 Słabe algorytmy i funkcje skrótu są obecnie używane do istnieje wiele możliwych przyczyn, ale nie powinny być używane, aby zagwarantować poufność danych, które chroni.  
  
 Reguła jest wyzwalane po znalezieniu 3DES, SHA1 lub RIPEMD160 algorytmy kod i zgłasza ostrzeżenia dla użytkownika.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Użyj kryptograficznie silniejszych opcji:  
  
-   Do szyfrowania TripleDES, użyj <xref:System.Security.Cryptography.Aes> szyfrowania.  
  
-   Dla funkcji skrótu SHA1 lub RIPEMD160, użyj tych w [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) rodziny (np. <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomiń ostrzeżenie od tej reguły, jeśli poziom zabezpieczeń dla danych nie wymaga gwarancji bezpieczeństwa.  
  
## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod  
 Począwszy od chwili pisania tego dokumentu poniższy przykład pseudo-kodu ilustruje wzorzec wykryte przez tę regułę.  
  
### <a name="sha-1-hashing-violation"></a>Naruszenie wyznaczania wartości skrótu SHA-1  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA1.Create();  
  
```  
  
### <a name="solution"></a>Rozwiązanie  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA256.Create();  
  
```  
  
### <a name="ripemd160-br-br-hashing-violation"></a>RIPEMD160 <br /><br />Naruszenie wyznaczania wartości skrótu  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = RIPEMD160Managed.Create();  
  
```  
  
### <a name="solution"></a>Rozwiązanie  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA256.Create();  
  
```  
  
### <a name="tripledes-encryption-violation"></a>TripleDES naruszenie szyfrowania  
  
```  
using System.Security.Cryptography;   
...    
using (TripleDES encAlg = TripleDES.Create())   
{   
  ...   
}  
```  
  
### <a name="solution"></a>Rozwiązanie  
  
```  
using System.Security.Cryptography;   
...   
using (AesManaged encAlg = new AesManaged())   
{   
  ...   
}  
```