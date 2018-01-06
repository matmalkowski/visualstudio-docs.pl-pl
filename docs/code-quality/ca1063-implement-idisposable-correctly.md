---
title: "CA1063: Zaimplementować interfejs IDisposable poprawnie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 33c9b3d7b3cdcfc49c3fac14e5ba3a2dcfc2fc49
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Należy prawidłowo zaimplementować interfejs IDisposable
|||  
|-|-|  
|TypeName|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 `IDisposable`Nie zaimplementowano poprawnie. Poniżej przedstawiono niektóre przyczyny tego problemu:  
  
-   Interfejs IDisposable, jest ponownie zaimplementowana w klasie.  
  
-   Finalizuj ponownie zostanie zastąpiona.  
  
-   Metoda Dispose zostanie zastąpiona.  
  
-   Metody Dispose() nie jest publiczny, zapieczętowany lub o nazwie Dispose.  
  
-   Dispose(bool) nie jest chroniony, wirtualny lub niezapieczętowany.  
  
-   Niezapieczętowane typy Dispose() musi wywołać metody Dispose(true).  
  
-   W przypadku typów niezapieczętowanych implementacji Finalize nie wywołuje jednego lub obu tych Dispose(bool) lub finalizator klasy case.  
  
 Naruszenie któregokolwiek z tych wzorców wyzwoli to ostrzeżenie.  
  
 Co głównego niezapieczętowany typ interfejsu IDisposable podać własną chronionych void Dispose(bool) metody wirtualnej. Metody Dispose() powinny wywoływać Dipose(true) i Finalize powinny wywoływać metody Dispose(false). Jeśli tworzysz typu IDisposable niezapieczętowany głównego należy zdefiniować Dispose(bool) i wywołać ją. Aby uzyskać więcej informacji, zobacz [czyszczenie zasobów niezarządzanych](/dotnet/standard/garbage-collection/unmanaged) w [zaleceń dotyczących projektowania Framework](/dotnet/standard/design-guidelines/index) części dokumentacji programu .NET Framework.  
  
## <a name="rule-description"></a>Opis reguły  
 Wszystkie typy IDisposable powinny poprawnie implementować wzorzec Dispose.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Sprawdź swój kod, aby ustalić, które z następujących rozwiązań naprawi to naruszenie.  
  
-   Usuń interfejs IDisposable z listy interfejsów implementowanych przez {0}, które override implementację metody Dispose klasy podstawowej.  
  
-   Usuń finalizator z typu {0}, Przesłoń metodę Dispose (bool disposing) i umieść logikę finalizowania w ścieżce kodu, w którym "disposing" ma wartość false.  
  
-   Usuń {0}, Przesłoń metodę Dispose (bool disposing) i umieść logikę rozporządzania w ścieżce kodu, w którym "disposing" ma wartość true.  
  
-   Upewnij się, że {0} jest zadeklarowany jako publiczny i zapieczętowany.  
  
-   Zmień nazwę "Dispose" {0} i upewnij się, że jest on zadeklarowany jako publiczny i zapieczętowany.  
  
-   Upewnij się, że {0} jest zadeklarowany jako chroniony, wirtualny i niezapieczętowany.  
  
-   Tak, aby wywołuje metody Dispose(true), następnie wywołuje GC, należy zmodyfikować {0}. Metodę SuppressFinalize w bieżącym wystąpieniu obiektu ("this" lub "Me" w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), a następnie zwraca.  
  
-   Tak, aby wywołuje metody Dispose(false), a następnie zwraca, należy zmodyfikować {0}.  
  
-   Jeśli piszesz klasy interfejsu IDisposable niezapieczętowany głównego upewnij się, że implementacja interfejsu IDisposable zgodny ze wzorcem opisanego wcześniej w tej sekcji.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod  
 Poniższy pseudo-kod zawiera ogólne przykład implementowania Dispose(bool) w klasie, która używa zarządzane i natywne zasoby.  
  
```  
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