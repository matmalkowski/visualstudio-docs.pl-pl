---
title: 'CA1811: Unikaj niewywołanego kodu prywatnego'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7f31b27740b286065221838e733d99e94b3307d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Unikaj niewywołanego kodu prywatnego
|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Prywatny lub wewnętrzny elementu członkowskiego (poziomu zestawu) nie ma obiektów wywołujących w zestawie, nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego i nie jest wywoływany przez obiekt delegowany. Następujące elementy członkowskie nie są sprawdzane przez tę regułę:

-   Elementy członkowskie interfejsu jawnego.

-   Konstruktory statyczne.

-   Konstruktory serializacji.

-   Metody oznaczone atrybutami <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> lub <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

-   Elementy członkowskie, które są zastąpienia.

## <a name="rule-description"></a>Opis reguły
 Ta zasada może raportować się, że wyniki fałszywie dodatnie, jeśli wystąpią punkty wejścia, które nie zostaną rozpoznane przez logikę reguł. Ponadto kompilatora może wyemitować kodu noncallable w zestawie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, Usuń noncallable kod lub Dodaj kod, który wywołuje go.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły.

## <a name="related-rules"></a>Powiązanych reguł
 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)