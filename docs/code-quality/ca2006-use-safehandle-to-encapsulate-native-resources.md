---
title: 'CA2006: Użyj SafeHandle, aby hermetyzować zasoby natywne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 4183828b4deddede919ea30db825e65f0360adef
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915050"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Użyj SafeHandle, aby hermetyzować zasoby natywne
|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategoria|Microsoft.Reliability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Zarządzany kod używa <xref:System.IntPtr> dostęp do zasobów macierzystych.

## <a name="rule-description"></a>Opis reguły
 Użycie `IntPtr` w kodzie zarządzanym może wskazywać na potencjalny problem bezpieczeństwa i niezawodności. Wszystkie użycia `IntPtr` musi sprawdzić tak, aby określić, czy użycie <xref:System.Runtime.InteropServices.SafeHandle> , lub podobnych technologii, jest wymagana w tym miejscu. Jeśli będą powodować problemy `IntPtr` reprezentuje niektórych zasób macierzysty, np. pamięci, dojście do pliku lub gniazdo, że kod zarządzany jest uznawany za własnych. Jeśli kod zarządzany jest właścicielem zasobu, jego również zwolnić natywne zasoby skojarzone z nią, ponieważ błąd w tym celu spowodowałoby przecieków zasobów.

 W takich scenariuszach problemy z zabezpieczeniami lub niezawodności będzie również istnieć jeśli wielowątkowych dostęp do `IntPtr` i sposób zwolnienia zasobu reprezentowanego przez `IntPtr` jest dostępne. Te problemy obejmują recyklingu `IntPtr` wartość w wersji zasobów w trakcie równoczesne używanie zasobu w innym wątku. Może to spowodować wyścigu, gdy jeden wątek może odczytu lub zapisu danych, który jest skojarzony z niewłaściwego zasobu. Na przykład, jeśli z danym typem przechowuje dojście systemu operacyjnego jako `IntPtr` i umożliwia użytkownikom wywołać metodę **Zamknij** i innych metod, które używa tego dojścia jednocześnie i bez określonego rodzaju synchronizacji, kod ma uchwyt odtwarzania Wystąpił problem.

 Ta dojścia odtwarzania problem może spowodować uszkodzenie danych i często luki w zabezpieczeniach. `SafeHandle` i klasa jego element równorzędny <xref:System.Runtime.InteropServices.CriticalHandle> udostępniają mechanizm Hermetyzowanie uchwyt macierzysty do zasobu, aby uniknąć tych problemów wątków. Ponadto można użyć `SafeHandle` i jego klasa element równorzędny `CriticalHandle` innych wątków problemów, na przykład jest ścisła kontrola okres istnienia obiektów zarządzanych, które zawierają kopię uchwyt macierzysty za pośrednictwem wywołania metod natywnych. W takiej sytuacji można często wyeliminować wywołania `GC.KeepAlive`. Większe obciążenie wydajności ponosisz, korzystając z `SafeHandle` i w mniejszym stopniu `CriticalHandle`, często można zmniejszyć za pomocą zachować ostrożność podczas projektowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Konwertuj `IntPtr` wykorzystania `SafeHandle` bezpieczne zarządzanie dostępem do zasobów natywnych. Zobacz <xref:System.Runtime.InteropServices.SafeHandle> temat referencyjny przykłady.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie należy pominąć to ostrzeżenie.

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable>