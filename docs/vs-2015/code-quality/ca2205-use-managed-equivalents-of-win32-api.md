---
title: 'CA2205: Użyj zarządzanych odpowiedników interfejsu API Win32 | Dokumentacja firmy Microsoft'
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
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 98c32eb197bb644d0e540bccea10603217342642
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902983"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Użyj zarządzanych odpowiedników interfejsu API Win32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2205: Użyj zarządzanych odpowiedników interfejsu API Win32](https://docs.microsoft.com/visualstudio/code-quality/ca2205-use-managed-equivalents-of-win32-api).

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Wywołania platformy zdefiniowano metody, które metody z równoważną funkcjonalność istnieje w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] biblioteki klas.

## <a name="rule-description"></a>Opis reguły
 Metoda wywołania platformy służy do wywoływania niezarządzanych funkcji DLL i jest definiowana za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybut, lub `Declare` — słowo kluczowe w języku Visual Basic. Platforma nieprawidłowo zdefiniowana invoke, metoda może prowadzić do wyjątki środowiska uruchomieniowego ze względu na problemy, takie jak funkcja misnamed wadliwe mapowania typów danych wartości parametrów i zwrotu i specyfikacji nieprawidłowe pola, takie jak Konwencja wywoływania i znak zestaw. Jeśli to możliwe, jest zazwyczaj łatwiejsze i mniej podatne do wywoływania metody zarządzanych równoważne niż do definiowania i bezpośrednio wywoływać metody niezarządzanego. Wywołanie platformy Wywołaj metodę również może prowadzić do problemów zabezpieczeń, które powinny być usuwane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Zastąp wywołanie do funkcji niezarządzanych przy użyciu wywołania na odpowiadającą jej zarządzanych.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, jeśli metody sugerowane zastępowania nie udostępnia wymaganych funkcji.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano, a platforma wywołać definicję metody, która narusza regułę. Dodatkowo wywołania platformy wywołania metody i są wyświetlane równoważne zarządzaną metodą.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1404: Wywołaj metodę GetLastError natychmiast po P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: Przenieś P/Invokes do klasy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Powinny istnieć punkty wejścia P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invokes nie powinny być widoczne](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Określ marshaling dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)



