---
title: CA5351 Nie używaj przerwane algorytmy kryptograficzne
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3aa720459fff6cc67080fd3368cda6ed3a82bfda
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920421"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351 Nie używaj przerwane algorytmy kryptograficzne
|||
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351|
|Kategoria|Microsoft.Cryptography|
|Zmiana kluczowa|Bez podziału|

> [!NOTE]
>  To ostrzeżenie Data ostatniej aktualizacji listopada 2015 r.

## <a name="cause"></a>Przyczyna
 Generowanie skrótów funkcji, takich jak <xref:System.Security.Cryptography.MD5> i algorytmów szyfrowania, takich jak <xref:System.Security.Cryptography.DES> i <xref:System.Security.Cryptography.RC2> mogą uwidaczniać znaczące zagrożenie i może spowodować narażenie poufne informacje za pomocą techniki trivial ataku, takimi jak ataki siłowe i kolizji wyznaczania wartości skrótu.

 Na poniższej liście algorytmy kryptograficzne są narażone na ataki kryptograficzne znane. Algorytm skrótu kryptograficznego <xref:System.Security.Cryptography.MD5> jest podatna na ataki kolizji wyznaczania wartości skrótu.  W zależności od użycia kolizji skrótu może prowadzić do personifikacji, zmanipulowaniem lub inne rodzaje ataków na systemy, które opierają się na unikatowe dane wyjściowe kryptograficznych funkcji skrótu. Algorytmy szyfrowania <xref:System.Security.Cryptography.DES> i <xref:System.Security.Cryptography.RC2> są narażone na ataki kryptograficzne, które mogą spowodować niezamierzone ujawnienie zaszyfrowanych danych.

## <a name="rule-description"></a>Opis reguły
 Uszkodzony kryptograficznych algorytmy nie są uznawane za bezpieczne i należy go unikać ich używania. Algorytm wyznaczania wartości skrótu MD5 jest narażony na ataki kolizji znane, że różni się zależnie od kontekstu Użyj określonych luk w zabezpieczeniach.  Algorytmami wyznaczania wartości skrótu używany w celu zapewnienia integralności danych (np. podpis pliku lub certyfikatu cyfrowego) są szczególnie podatne.  W tym kontekście osoby atakujące może wygenerować dwa osobne fragmenty danych, tak, aby niegroźne danych można zastąpić szkodliwe dane bez konieczności zmiany wartości skrótu lub unieważnienie skojarzonego podpisu cyfrowego.

 Dla algorytmów szyfrowania:

-   <xref:System.Security.Cryptography.DES> szyfrowanie zawiera mały rozmiar klucza, który może być metodą siłową wymuszone w ciągu Niecałego dnia.

-   <xref:System.Security.Cryptography.RC2> Szyfrowanie jest narażony na ataki związane z kluczem, jeśli osoba atakująca stwierdzi matematyczne relacje między wszystkie wartości klucza.

 Ta zasada wyzwala znajduje powyżej funkcje kryptograficzne w kodzie źródłowym i zgłasza ostrzeżenia dla użytkownika.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Użyj kryptograficznie silniejszych opcji:

-   MD5, użyj wartości skrótów w [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) rodziny (np. <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

-   DES i RC2, użyj <xref:System.Security.Cryptography.Aes> szyfrowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia od tej reguły, chyba że jest zostały sprawdzone przez ekspertów kryptograficznych.

## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod
 Poniższy przykład pseudo-kodu ilustruje wzorzec wykryte przez reguły i możliwych alternatyw.

### <a name="md5-hashing-violation"></a>MD5 Naruszenie wyznaczania wartości skrótu

```
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();

```

### <a name="solution"></a>Rozwiązanie

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="rc2-encryption-violation"></a>RC2 Naruszenie szyfrowania

```
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();

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

### <a name="des-br-br-encryption-violation"></a>DES <br /><br />Naruszenie szyfrowania

```
using System.Security.Cryptography;
...
DES encAlg = DES.Create();

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