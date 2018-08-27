---
title: Programy obsługi zdarzeń propagujące zmiany poza modelem
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ac748cae6bf36a95b95c5d9a27aa9469ae440eed
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953636"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Programy obsługi zdarzeń propagujące zmiany poza modelem

W wizualizacji i modelowania zestawu SDK, można zdefiniować magazynu obsługi zdarzeń do propagujące zmiany do zasobów poza magazynu, na przykład zmienne bez magazynu, plików modeli w innych magazynach lub inne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenia. Programy obsługi zdarzeń magazynu są wykonywane po zakończeniu transakcji, w którym wystąpiło zdarzenie wyzwalania. Są one również wykonywane Cofnij lub ponów operację. W związku z tym w przeciwieństwie do reguł magazynu zdarzenia magazynu są najbardziej przydatny w przypadku aktualizowania wartości, które znajdują się poza Sklepem. W przeciwieństwie do zdarzenia platformy .NET magazynu obsługi zdarzeń są rejestrowane nasłuchiwanie na klasę: nie trzeba zarejestrować oddzielne obsługi dla poszczególnych wystąpień. Aby uzyskać więcej informacji o tym, jak wybrać różne sposoby obsługi zmian, zobacz [reagowania na zagrożenia i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).

Powierzchni graficznego i innych kontrolek interfejsu użytkownika są przykładami zasobów zewnętrznych, które są obsługiwane przez zdarzenia magazynu.

### <a name="to-define-a-store-event"></a>Aby zdefiniować zdarzenia magazynu

1.  Wybierz typ zdarzenia, które chcesz monitorować. Aby uzyskać pełną listę przyjrzeć się właściwości <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Każda właściwość odnosi się do typu zdarzenia. Najczęściej używane zdarzenie, które typy to:

    -   `ElementAdded` -wyzwalane, gdy element modelu, łącze relacji, łącznik lub kształt jest tworzony.

    -   ElementPropertyChanged - wyzwalane, gdy wartość `Normal` właściwość domeny zostanie zmieniona. Zdarzenie jest wywoływane tylko wtedy, gdy wartości nowym i starym nie są takie same. Nie można zastosować zdarzenie do właściwości magazynu obliczeniowej i niestandardowe.

         Nie można zastosować do właściwości roli, które odpowiadają łącza relacji. Zamiast tego należy użyć `ElementAdded` do monitorowania relacji domeny.

    -   `ElementDeleted` -wyzwalane po element modelu, relację, kształtu lub łącznik został usunięty. Nadal możesz uzyskać dostępu do wartości właściwości elementu, ale go nie odniesie żadnych relacji z innymi elementami.

2.  Dodaj definicję klasy częściowej dla *YourDsl *** DocData** w osobnym pliku kodu w **DslPackage** projektu.

3.  Pisanie kodu zdarzenia metodą, jak w poniższym przykładzie. Można ją `static`, chyba że chcesz uzyskać dostęp do `DocData`.

4.  Zastąpienie `OnDocumentLoaded()` zarejestrować program obsługi. Jeśli masz więcej niż jednej procedury obsługi, można je zarejestrować w tym samym miejscu.

Lokalizacja kodu rejestracji nie jest krytyczne. `DocView.LoadView()` jest alternatywną lokalizację.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don't forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }
}
```

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Korzystaj ze zdarzeń, aby dostosować nieodwracalna w magazynie

Zdarzenia magazynu nie są zwykle używane dla propagowanie zmian w magazynie, ponieważ program obsługi zdarzeń jest wykonywany po transakcja została przekazana. Zamiast tego czy należy użyć reguły magazynu. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

Można jednak użyć program obsługi zdarzeń do wprowadzania dodatkowych aktualizacji do magazynu, jeśli użytkownik ma będzie można cofnąć dodatkowych aktualizacji niezależnie od oryginalnej zdarzeń. Załóżmy na przykład, czy standardowej Konwencji dla albumów małych liter. Można zapisać magazynu obsługi zdarzeń, która naprawia tytuł na małe litery, po użytkownika został wpisany wielkimi literami. Jednak użytkownik może użyć polecenia Cofnij anulować poprawkę, przywracanie wielkich liter. Drugi cofania spowoduje usunięcie użytkownika zmiany.

Z kolei zapisano regułę magazynu, aby zrobić to samo, użytkownika zmiany i poprawki działałoby w tej samej transakcji, dzięki czemu użytkownik nie może cofnąć dostosowania bez utraty oryginalnego zmiany.

```csharp
partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}
```

Jeśli piszesz zdarzenie aktualizacji magazynu:

-   Użyj `store.InUndoRedoOrRollback` w celu uniknięcia wprowadzania zmian do elementów modelu w cofania. Menedżer transakcji ustawi wszystko w magazynie do stanu pierwotnego.

-   Użyj `store.InSerializationTransaction` w celu uniknięcia wprowadzanie zmian w czasie ładowania modelu z pliku.

-   Zmiany spowoduje dalsze zdarzenia, które będą wyzwalane. Upewnij się, że należy unikać nieskończoną pętlę.

## <a name="store-event-types"></a>Przechowywanie typów zdarzeń

Każdy typ zdarzenia odnosi się do kolekcji w Store.EventManagerDirectory. Można dodawać i usuwać programów obsługi zdarzeń w dowolnym momencie, ale jest zwykle je dodać podczas ładowania dokumentu.

|`EventManagerDirectory` Nazwa właściwości|Gdy wykonywane|
|-------------------------------------------|-------------------|
|ElementAdded|Tworzone jest wystąpienie klasy domeny, relacji domeny, kształtu, łącznik lub diagramu.|
|ElementDeleted|Element modelu został usunięty z katalogu elementu magazynu i nie jest już źródłowa lub docelowa żadnych relacji. Element faktycznie nie zostanie usunięty z pamięci, ale jest zachowane w przypadku przyszłych operacji cofania.|
|ElementEventsBegun|Wywoływane na końcu transakcji zewnętrznej.|
|ElementEventsEnded|Wywoływane, gdy inne zdarzenia zostały przetworzone.|
|ElementMoved|Element modelu został przeniesiony z jednego magazynu partycji do innej.<br /><br /> To nie jest powiązana z lokalizacji kształt na diagramie.|
|ElementPropertyChanged|Wartość właściwości domeny została zmieniona. Jest to wykonywane tylko wtedy, gdy starej i nowej wartości są równe.|
|RolePlayerChanged|Jedną z dwóch ról relacji (kończy się) odwołuje się do nowego elementu.|
|RolePlayerOrderChanged|W roli o liczebności większej niż 1 sekwencja łącza została zmieniona.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Zobacz też

- [Odpowiadanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md)
- [Przykładowy kod: diagramy obwodu](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]