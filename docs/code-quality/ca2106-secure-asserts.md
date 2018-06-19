---
title: 'CA2106: Potwierdzanie zabezpieczeń'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5863f4d8ca4db47f7e537f0b1abc5eb280434c80
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916802"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Potwierdzanie zabezpieczeń
|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda potwierdza uprawnienia i żadne sprawdzenia zabezpieczeń nie są wykonywane na obiekcie wywołującym.

## <a name="rule-description"></a>Opis reguły
 Potwierdzanie uprawnienia zabezpieczeń bez sprawdzania zabezpieczeń może pozostawić zdatną do wykorzystania słabość zabezpieczeń w kodzie. Przeszukiwania stosu zabezpieczeń zatrzymywana, gdy jest potwierdzone uprawnienia zabezpieczeń. Jeśli uprawnienie jest assert bez wykonywania jakiejkolwiek kontroli wywołującego, wywołujący pośrednio wykonanie kodu przy użyciu uprawnień. Potwierdza bez sprawdzania zabezpieczeń są dopuszczalne, tylko jeśli masz pewność, że assert nie można użyć w szkodliwy sposób. Assert jest bezpieczne, jeśli kod, który można wywołać jest nieszkodliwy lub użytkownicy nie można przekazać dowolnych informacji do kodu, który można wywołać.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj żądania zabezpieczeń do metody lub jej typ deklarujący.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie od tej zasady tylko po dokonaniu przeglądu zabezpieczeń zachować ostrożność.

## <a name="see-also"></a>Zobacz też
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)