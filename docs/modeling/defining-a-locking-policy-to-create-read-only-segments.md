---
title: Definiowanie zasad blokowania na potrzeby tworzenia segmentów tylko do odczytu
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 48a9ebdf7df8e03813e1819e907c9aab2d558ee0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953600"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definiowanie zasad blokowania na potrzeby tworzenia segmentów tylko do odczytu
Interfejs API Immutability z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wizualizacji i modelowania zestaw SDK umożliwia programowi blokady części lub całości modelu języka specyficznego dla domeny (DSL), dzięki czemu można odczytać ale niezmienione. Ta opcja tylko do odczytu mogą służyć, na przykład, aby użytkownik poproś współpracowników, aby dodawać adnotacje i przejrzeć modelu DSL, ale można uniemożliwić ich zmianę oryginalnej.

 Ponadto, ponieważ autor DSL, można zdefiniować *zasad blokowania.* Zasady blokowania definiuje, które blokady są dozwolone, niedozwolone lub obowiązkowe. Na przykład podczas publikowania DSL może zwiększyć deweloperów innych firm do jego rozszerzenia z nowych poleceń. Jednak aby uniemożliwić zmianę stanu tylko do odczytu określonego części modelu można użyć również zasad blokowania.

> [!NOTE]
>  Zasady blokowania można obejść przy użyciu odbicia. Udostępnia wyraźne granice dla deweloperów innych firm, ale nie zapewnia dużego bezpieczeństwa.

 Więcej informacji oraz przykłady są dostępne w programie Visual Studio [wizualizacji i modelowania SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) witryny sieci Web.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Ustawiania i pobierania blokady
 Można ustawić blokady w magazynie, partycji lub pojedynczy element. Na przykład tej instrukcji będzie zapobiec usunięciu elementu modelu, a także uniemożliwi jej właściwości zmieniane:

```
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Inne wartości blokady można zapobiec zmianom w relacji, tworzenie elementu ruchu między partycji i ponownie porządkowania łącza w roli.

 Blokad, stosuje się do akcji użytkownika i kodu programu. Jeśli kod programu podejmuje próbę dokonania zmiany, `InvalidOperationException` zostanie wygenerowany. Blokady są ignorowane w Cofnij lub ponów operację.

 Można wykryć, czy element ma wszystkie blokady w danym zestawie przy użyciu `IsLocked(Locks)` i bieżącego zestawu blokad w elemencie można uzyskać za pomocą `GetLocks()`.

 Można ustawić blokady bez przy użyciu transakcji. Blokady bazy danych nie jest częścią sklepu. Jeśli ustawisz blokady w odpowiedzi na zmianę wartości w magazynie, na przykład w OnValueChanged, należy zezwalać na zmiany, które są częścią operacji cofania.

 Te metody są metody rozszerzenia, które są zdefiniowane w <xref:Microsoft.VisualStudio.Modeling.Immutability> przestrzeni nazw.

### <a name="locks-on-partitions-and-stores"></a>Blokad na partycje i magazynów
 Blokady można również będą stosowane do partycji i magazynu. Blokady, która jest ustawiona na partycji ma zastosowanie do wszystkich elementów w partycji. W związku z tym na przykład następująca instrukcja uniemożliwi wszystkie elementy w partycji usuwane niezależnie od stanów własnych blokad. Niemniej jednak inne blokuje takie jak `Locks.Property` nadal mógł zostać ustawiony na poszczególne elementy:

```
partition.SetLocks(Locks.Delete);
```

 Blokada jest ustawiony na magazynie ma zastosowanie do wszystkich swoich elementów, niezależnie od ustawienia tej blokady na partycje i elementów.

### <a name="using-locks"></a>Przy użyciu blokady
 Można użyć blokady wdrożenie systemów, takich jak następujące przykłady:

-   Nie zezwalaj na zmiany do wszystkich elementów i relacji z wyjątkiem tych, które reprezentują komentarze. Dzięki temu użytkownicy mogą dodawać adnotacje modelu bez jego zmiany.

-   Nie zezwalaj na zmiany w domyślnej partycji, ale pozwala na wprowadzanie zmian w partycji diagramu. Użytkownik może zmienić diagramu, ale nie można zmienić modelu źródłowego.

-   Nie zezwalaj na zmiany do magazynu, z wyjątkiem grupy użytkowników, którzy są zarejestrowane w oddzielnej bazy danych. Dla innych użytkowników diagram i model są tylko do odczytu.

-   Nie zezwalaj na zmiany w modelu, jeśli właściwość logiczna diagramu jest ustawiona na true. Podaj polecenie, aby zmienić tej właściwości. Dzięki temu użytkownicy, którzy nie wprowadzaj zmian przypadkowo.

-   Nie zezwalaj na dodawanie i usuwanie elementów i relacje poszczególnych klas, ale zezwala na zmiany właściwości. Zapewnia to użytkownikom stałego formularza, w którym można wypełnić właściwości.

## <a name="lock-values"></a>Wartości blokady
 Można ustawić blokady na magazyn, partycji lub poszczególnych ModelElement. Blokady jest `Flags` wyliczenie: można łączyć przy użyciu wartości "&#124;".

-   Blokady ModelElement zawsze należy uwzględniać blokad jego partycji.

-   Blokady partycji zawsze należy uwzględniać blokad magazynu.

 Nie można ustawić blokady na partycji lub przechowywać i w tym samym czasie wyłączyć blokadę pojedynczy element.

|Wartość|Co oznacza, jeśli `IsLocked(Value)` ma wartość true|
|-----------|------------------------------------------|
|Brak|Bez ograniczeń.|
|Właściwość|Nie można zmienić właściwości domeny elementów. Dotyczy to właściwości, które są generowane przez rolę klasy domeny w relacji.|
|Dodaj|Nie można utworzyć nowych elementów i linki w partycji lub przechowywania.<br /><br /> Nie dotyczy `ModelElement`.|
|Przenieś|Nie można przenieść elementu między partycji, jeśli `element.IsLocked(Move)` ma wartość true, lub jeśli `targetPartition.IsLocked(Move)` ma wartość true.|
|Usuwanie|Nie można usunąć elementu, jeśli ustawiono blokady tego samego elementu, lub na każdym z elementów, do którego będzie propagowane usunięcia, takich jak elementy osadzone i kształtów.<br /><br /> Można użyć `element.CanDelete()` Aby dowiedzieć się, czy element może zostać usunięte.|
|Zmiana kolejności|Nie można zmienić kolejności łączy w roleplayer.|
|RolePlayer|Nie można zmienić zestaw linki, które biorą się w tym elemencie. Na przykład nowe elementy nie mogą być osadzone w tym elemencie. Nie dotyczy to łącza, dla którego ten element jest elementem docelowym.<br /><br /> Jeśli ten element jest łączem, jego źródło i cel nie dotyczy.|
|Wszystkie|Bitowe lub innych wartości.|

## <a name="locking-policies"></a>Zasady blokowania
 Jako autor DSL, można zdefiniować *zasad blokowania*. Zasady blokowania łagodzi warunki operacji SetLocks(), dzięki czemu użytkownik może uniemożliwić określonych blokad ustawić lub wprowadzić określonych blokady musi być ustawiona. Zazwyczaj należy użyć zasad blokowania, aby zniechęcać użytkowników lub deweloperzy z przypadkowo naruszeniem zamierzonym użyciem DSL, w taki sam sposób, że można zadeklarować zmiennej `private`.

 Umożliwia także zasady blokowania można ustawić blokady na wszystkie elementy zależne od typu elementu. Jest to spowodowane `SetLocks(Locks.None)` zawsze jest wywoływane, gdy element jest najpierw utworzyć lub deserializacji z pliku.

 Nie można jednak użyć zasad różnicującej podczas jej trwania blokady w elemencie. Aby osiągnąć ten efekt, należy użyć wywołania `SetLocks()`.

 Aby zdefiniować zasady blokowania, konieczne będzie:

-   Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.

-   Dodaj tę klasę do usług, które są dostępne za pośrednictwem DocData Twoje DSL.

### <a name="to-define-a-locking-policy"></a>Do zdefiniowania zasad blokowania
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> ma następującą definicję:

```
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Te metody są wywoływane, gdy połączenie jest nawiązywane w przypadku `SetLocks()` w magazynie, partycji lub ModelElement. W każdej metody są dostarczane z zestawem proponowanych blokad. Można zwrócić zestaw proponowanych lub można dodawać i odejmować blokad.

 Na przykład:

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  public class MyLockingPolicy : ILockingPolicy
  {
    /// <summary>
    /// Moderate SetLocks(this ModelElement target, Locks locks)
    /// </summary>
    /// <param name="element">target</param>
    /// <param name="proposedLocks">locks</param>
    /// <returns></returns>
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)
    {
      // In my policy, users can never delete an element,
      // and other developers cannot easily change that:
      return proposedLocks | Locks.Delete);
    }
    public Locks RefineLocks(Store store, Locks proposedLocks)
    {
      // Only one user can change this model:
      return Environment.UserName == "aUser"
           ? proposedLocks : Locks.All;
    }

```

 Aby upewnić się, że użytkownicy zawsze można usuwać elementów, nawet jeśli inny kod wywołuje `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Aby uniemożliwić zmianę właściwości każdego elementu MyClass:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Aby udostępnić zasad jako usługa
 W Twojej `DslPackage` projekt, Dodaj nowy plik, który zawiera kod, który podobnego do następującego:

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  // Override the DocData GetService() for this DSL.
  internal partial class YourDslDocData // Change
  {
    /// <summary>
    /// Custom locking policy cache.
    /// </summary>
    private ILockingPolicy myLockingPolicy = null;

    /// <summary>
    /// Called when a service is requested.
    /// </summary>
    /// <param name="serviceType">Service requested</param>
    /// <returns>Service implementation</returns>
    public override object GetService(System.Type serviceType)
    {
      if (serviceType == typeof(SLockingPolicy)
       || serviceType == typeof(ILockingPolicy))
      {
        if (myLockingPolicy == null)
        {
          myLockingPolicy = new MyLockingPolicy();
        }
        return myLockingPolicy;
      }
      // Request is for some other service.
      return base.GetService(serviceType);
    }
}
```
