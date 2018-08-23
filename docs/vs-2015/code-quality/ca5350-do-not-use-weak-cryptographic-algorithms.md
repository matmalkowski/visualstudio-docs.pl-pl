---
title: 'CA5350: Nie używaj słabych algorytmów kryptograficznych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8321d94bbdcc66bb8e7405f2f3188ba3eeaaabd8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676543"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nie używaj słabych algorytmów kryptograficznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|CheckId|CA5350|  
|Kategoria|Microsoft.Cryptography|  
|Zmiana kluczowa|Bez podziału|  
  
> [!NOTE]
>  To ostrzeżenie Data ostatniej aktualizacji listopada 2015 r.  
  
## <a name="cause"></a>Przyczyna  
 Algorytmy szyfrowania, takich jak <xref:System.Security.Cryptography.TripleDES> i algorytmy wyznaczania wartości skrótu takich jak <xref:System.Security.Cryptography.SHA1> i <xref:System.Security.Cryptography.RIPEMD160> są uważane za słabe.  
  
 Te algorytmy kryptograficzne nie oferuje tylu Gwarancja bezpieczeństwa jako odpowiednikami nowocześniejszego. Kryptograficznych, algorytmy wyznaczania wartości skrótu <xref:System.Security.Cryptography.SHA1> i <xref:System.Security.Cryptography.RIPEMD160> zapewniają odporność kolizji, mniej niż bardziej nowoczesne algorytmy wyznaczania wartości skrótu. Algorytm szyfrowania <xref:System.Security.Cryptography.TripleDES> zapewnia mniejszą liczbę bitów zabezpieczeń niż bardziej nowoczesne algorytmy szyfrowania.  
  
## <a name="rule-description"></a>Opis reguły  
 Słabe szyfrowanie, algorytmy i funkcje wyznaczania wartości skrótu są używane obecnie do szeregu przyczyn, ale nie powinny one być używane dla zagwarantowania poufności danych, które chronią.  
  
 Reguła wyzwalania, gdy znajdzie 3DES, SHA1 lub RIPEMD160 algorytmów w kodzie i zgłoszenie ostrzeżenia dla użytkownika.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Użyj kryptograficznie silniejszych opcji:  
  
-   W przypadku szyfrowania TripleDES, użyj <xref:System.Security.Cryptography.Aes> szyfrowania.  
  
-   Dla funkcji skrótu SHA1 lub RIPEMD160, użyj tych w [SHA-2](https://msdn.microsoft.com/en-us/library/windows/desktop/aa382459.aspx) rodziny (np. <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomijaj ostrzeżeń dla tej reguły, jeśli poziom ochrony danych przez nie wymaga gwarancji bezpieczeństwa.  
  
## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod  
 Począwszy od chwili pisania tego dokumentu Poniższy przykładowy pseudo-kod przedstawiono wzorzec wykryte przez tę regułę.  
  
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
  
### <a name="tripledes-encryption-violation"></a>TripleDES szyfrowania naruszenia  
  
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