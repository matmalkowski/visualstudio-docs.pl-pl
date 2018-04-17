---
title: 'CA1063: Zaimplementować interfejs IDisposable poprawnie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/12/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 993e3f01d040c6576c497b43442f9c348c3b4521
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Należy prawidłowo zaimplementować interfejs IDisposable

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

`IDisposable` Nie zaimplementowano poprawnie. Poniżej przedstawiono niektóre przyczyny tego problemu:

- Interfejs IDisposable, jest ponownie zaimplementowana w klasie.

- Finalizuj ponownie zostanie zastąpiona.

- Metoda Dispose zostanie zastąpiona.

- Metody Dispose() nie jest publiczny, zapieczętowany lub o nazwie Dispose.

- Dispose(bool) nie jest chroniony, wirtualny lub niezapieczętowany.

- Niezapieczętowane typy Dispose() musi wywołać metody Dispose(true).

- W przypadku typów niezapieczętowanych implementacji Finalize nie wywołuje jednego lub obu tych Dispose(bool) lub finalizator klasy case.

Naruszenie któregokolwiek z tych wzorców wyzwoli to ostrzeżenie.

Co otwarty typ, który deklaruje i implementuje interfejs IDisposable, musisz podać własną chronionych void Dispose(bool) metody wirtualnej. Metody Dispose() powinny wywoływać Dipose(true) i Finalize powinny wywoływać metody Dispose(false). Jeśli tworzysz niezamknięty typ, który deklaruje i implementuje interfejs IDisposable, należy zdefiniować Dispose(bool) i wywołać ją. Aby uzyskać więcej informacji, zobacz [Oczyszczanie zasobów niezarządzanych](/dotnet/standard/garbage-collection/unmanaged) w [zaleceń dotyczących projektowania .NET Framework](/dotnet/standard/design-guidelines/index).

## <a name="rule-description"></a>Opis reguły

Wszystkie typy IDisposable powinny poprawnie implementować wzorzec Dispose.

## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń

Sprawdź swój kod, aby ustalić, które z następujących rozwiązań naprawi to naruszenie.

- Usuń interfejs IDisposable z listy interfejsów implementowanych przez {0}, które override implementację metody Dispose klasy podstawowej.

- Usuń finalizator z typu {0}, Przesłoń metodę Dispose (bool disposing) i umieść logikę finalizowania w ścieżce kodu, w którym "disposing" ma wartość false.

- Usuń {0}, Przesłoń metodę Dispose (bool disposing) i umieść logikę rozporządzania w ścieżce kodu, w którym "disposing" ma wartość true.

- Upewnij się, że {0} jest zadeklarowany jako publiczny i zapieczętowany.

- Zmień nazwę "Dispose" {0} i upewnij się, że jest on zadeklarowany jako publiczny i zapieczętowany.

- Upewnij się, że {0} jest zadeklarowany jako chroniony, wirtualny i niezapieczętowany.

- Tak, aby wywołuje metody Dispose(true), następnie wywołuje GC, należy zmodyfikować {0}. Metodę SuppressFinalize w bieżącym wystąpieniu obiektu ("this" lub "Me" w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), a następnie zwraca.

- Tak, aby wywołuje metody Dispose(false), a następnie zwraca, należy zmodyfikować {0}.

- Jeśli tworzysz niezamknięty typ, który deklaruje i implementuje interfejs IDisposable, upewnij się, że implementacja interfejsu IDisposable zgodny ze wzorcem opisanego wcześniej w tej sekcji.

## <a name="when-to-suppress-warnings"></a>Kiedy pomijanie ostrzeżeń

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod

Poniższy pseudo-kod zawiera ogólne przykład implementowania Dispose(bool) w klasie, która używa zarządzane i natywne zasoby.

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources itself, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```