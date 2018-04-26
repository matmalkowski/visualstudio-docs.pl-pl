---
title: Dostosowywanie zachowania dotyczącego usuwania
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9942d9903188785af1658a37515092c3ce1ad2dd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="customizing-deletion-behavior"></a>Dostosowywanie zachowania dotyczącego usuwania
Usunięcie elementu zwykle powoduje, że powiązanych elementów do usunięcia również. Wszystkie relacje dołączone do niego, a wszystkie elementy podrzędne zostaną usunięte. To zachowanie jest o nazwie *usunąć propagacji*. Można dostosować propagacji delete, na przykład ułożyć, że dodatkowe powiązane elementy są usuwane. Pisanie kodu programu, możesz wprowadzić propagacji delete są zależne od stanu modelu. Może również spowodować inne zmiany w odpowiedzi do usunięcia.

 Ten temat zawiera następujące sekcje:

-   [Sposób usuwania domyślne](#default)

-   [Ustawienie opcji Propaguj usuwanie roli](#property)

-   [Zastępowanie zamknięcia usunąć](#closure) -użyć tej metody, której usunięcia może prowadzić do usunięcia z sąsiadujących elementów.

-   [Przy użyciu OnDeleting i OnDeleted](#ondeleting) -użycia tych metod, w którym odpowiedzi może zawierać inne akcje, takie jak zaktualizowanie wartości lub spoza sklepu.

-   [Reguły usuwania](#rules) -Użyj reguł propagacji aktualizacji do dowolnego rodzaju w magazynie, w którym jednej zmiany może prowadzić do innych użytkowników.

-   [Usuwanie zdarzeń](#rules) -Użyj magazynu zdarzeń propagacji aktualizacji poza Sklepem, na przykład do innych [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dokumentów.

-   [Rozdziel](#unmerge) — za pomocą operacji Rozdziel cofnąć operację scalania, który dołączony do elementu nadrzędnego elementu podrzędnego.

##  <a name="default"></a> Sposób usuwania domyślne
 Domyślnie następujące zasady regulują propagacji usuwania:

-   Jeśli element zostanie usunięty, wszystkie elementy osadzone, również zostaną usunięte. Osadzone elementy są te, które są elementy docelowe relacji, dla których ten element jest źródłem osadzenia. Na przykład, jeśli istnieje relacja osadzania z **albumu** do **utworu**, a następnie usunięcie określonego albumu jego utworów muzycznych również zostaną usunięte.

     Z kolei usunięcie utworu nie powoduje usunięcia albumu.

-   Domyślnie usunięcia nie są propagowane wzdłuż relacji odwołania. Jeśli istnieje relacja odwołania **ArtistPlaysOnAlbum** z **albumu** do **wykonawcy**, usunięcie albumu nie powoduje usunięcia żadnych powiązanych wykonawcy i usuwanie wykonawcy nie Usuń wszelkie albumu.

     Jednak usunięcie propagację wzdłuż niektórych wbudowanych relacji. Na przykład po usunięciu elementu modelu są także usuwane jego kształtu na diagramie. Element i kształtu są powiązane przez `PresentationViewsSubject` relacji odwołania.

-   Co relacji, która jest połączona z elementu w ramach roli źródłowa lub docelowa jest usuwany. Właściwości roli elementu w ramach roli przeciwną nie zawiera już usuniętego elementu.

##  <a name="property"></a> Ustawienie opcji Propaguj usuwanie roli
 Może spowodować usunięcie na propagację wzdłuż relacja odwołania lub osadzonych podrzędnych do elementu nadrzędnego.

#### <a name="to-set-delete-propagation"></a>Aby ustawić propagacji delete

1.  Na diagramie definicji DSL wybierz *roli* do której należy propagacji do usunięcia. Rola jest reprezentowana przez wiersz po lewej lub prawej strony pola relacji domeny.

     Na przykład jeśli chcesz określić, że zawsze, gdy albumu zostanie usunięty, wykonawców powiązanych, również zostaną usunięte, a następnie wybierz rolę podłączone do klasy domeny wykonawcy.

2.  W oknie właściwości ustaw **propaguje usunąć** właściwości.

3.  Naciśnij klawisz F5 i sprawdź, czy:

    -   Po usunięciu wystąpienia tej relacji element w wybranej roli również zostaną usunięte.

    -   Po usunięciu elementu w ramach roli przeciwną wystąpienia tej relacji zostaną usunięte, a powiązane elementy w tej roli zostaną usunięte.

 Możesz również sprawdzić **propaguje usunąć** opcji **szczegóły DSL** okna. Wybierz klasę domeny, a następnie w oknie Szczegóły DSL Otwórz **Usuń zachowanie** strony przez kliknięcie przycisku po stronie okna. **Propagowany** opcja będzie wyświetlana dla funkcję przeciwną każdej relacji. **Usuń styl** kolumna wskazuje, czy **propagowany** opcji znajduje się na jego ustawienie domyślne, ale nie ma żadnego efektu oddzielne.

## <a name="delete-propagation-by-using-program-code"></a>Usuwanie propagacji przy użyciu kodu programu
 Opcje w pliku definicji DSL umożliwiają tylko wybierz, czy usunięcie propaguje do natychmiastowego sąsiada. Aby zaimplementować schemat bardziej złożonych propagacji delete, można napisać kod programu.

> [!NOTE]
>  Aby dodać kod programu do definicji DSL, Utwórz osobnym pliku kodu w **Dsl** projektu i zapisu częściowe definicje, aby rozszerzyć klasy w folderze wygenerowany kod. Aby uzyskać więcej informacji, zobacz [pisanie kodu, aby dostosować języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md).

##  <a name="closure"></a> Definiowanie zamknięcia Delete
 Operacja usunięcia używa klasy *YourModel *** DeleteClosure** Aby określić, które elementy, aby usunąć, biorąc pod uwagę wartości początkowe. Wywołuje `ShouldVisitRelationship()` i `ShouldVisitRolePlayer()` , przejście na wykresie relacji. Można zastąpić te metody. ShouldVisitRolePlayer jest dostarczany z tożsamości łącza i elementu w jednej z ról łącza. Powinien on zwrócić jedną z następujących wartości:

-   **VisitorFilterResult.Yes**— element powinien zostać usunięty, i walkera powinno być kontynuowane, aby wypróbować inne łącza do elementu.

-   **VisitorFilterResult.DoNotCare** — element nie należy go usunąć, chyba że inne zapytanie odpowiedzi na to, że należy ją usunąć.

-   **VisitorFilterResult.Never** — element nie należy usuwać, nawet wtedy, gdy odbierze inne zapytanie **tak**, i nie należy spróbować walkera elementu przez inne łącza.

```
// When a musician is deleted, delete their albums with a low rating.
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs
partial class MusicLibDeleteClosure
{
  public override VisitorFilterResult ShouldVisitRolePlayer
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)
  {
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;
    if (link != null
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)
    {
      // Count other unvisited links to the Album of this link.
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)
              .Where(linkAlbumArtist =>
                     linkAlbumArtist != link &&
                     !walker.Visited(linkAlbumArtist))
              .Count() == 0)
      {
        // Should delete this role player:
        return VisitorFilterResult.Yes;
      }
      else
        // Don't delete unless another relationship deletes it:
        return VisitorFilterResult.DoNotCare;
    }
    else
    {
      // Test for and respond to other relationships and roles here.

      // Not the relationship or role we're interested in.
      return base.ShouldVisitRolePlayer(walker, sourceElement,
             elementLink, targetDomainRole, targetRolePlayer);
    }
  }
}

```

 Metoda zamknięcia zapewnia ustalona zestaw elementów i linki, które mają zostać usunięte przed rozpoczęciem usunięcia. Walkera również łączy wyniki z zamknięcia z właściwościami z innych części modelu.

 Jednak techniki przyjęto założenie, że usunięcie dotyczy tylko jej sąsiadami na wykresie relacji: nie można użyć tej metody, aby usunąć element w innej części modelu. Nie można używać go, jeśli chcesz dodać elementy lub wprowadzić inne zmiany w odpowiedzi na usunięcie.

##  <a name="ondeleting"></a> Przy użyciu OnDeleting i OnDeleted
 Można zastąpić `OnDeleting()` lub `OnDeleted()` w klasie domeny lub w relacji domeny.

1.  <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> jest wywoływana, gdy element ma zostać usunięty, ale przed jego relacje został odłączony. Nadal można nawigować do i z innych elementów i jest nadal w `store.ElementDirectory`.

     Jeśli niektóre elementy są usuwane w tym samym czasie, OnDeleting jest wywoływana przed wykonaniem operacji usuwania dla wszystkich z nich.

     `IsDeleting` ma wartość true.

2.  <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> jest wywoływane, gdy element został usunięty. Pozostaje w stercie CLR, aby cofania można przeprowadzić, jeśli jest to wymagane, ale jest rozłączony z innymi elementami i usunięta z `store.ElementDirectory`. W przypadku relacji role nadal odwoływać się do starego pełniących role.`IsDeleted` ma wartość true.

3.  OnDeleting i OnDeleted są wywoływane, gdy użytkownik wywoła cofania po utworzeniu elementu i usuwanie wcześniejszych jest powtarzany w operacji ponownego wykonywania. Użyj `this.Store.InUndoRedoOrRollback` w celu uniknięcia aktualizowanie elementów magazynu w tych przypadkach. Aby uzyskać więcej informacji, zobacz [porady: użycie transakcji do aktualizacji modelu](../modeling/how-to-use-transactions-to-update-the-model.md).

 Na przykład następujący kod usuwa albumu po usunięciu jej ostatniego elementu podrzędnego utworu:

```

// Delete the parent Album when the last Song is deleted.
// Override methods in the embedding relationship between Album and Song:
partial class AlbumHasSongs
{
  protected override void OnDeleted()
  {
    base.OnDeleted();
    // Don't perform in-store actions in undo:
    if (this.Store.InUndoRedoOrRollback) return;
    // Relationship source and target still work:
    // Don't bother if source is already on its way out:
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)
    {
      if (this.Album.Songs.Count == 0)
      {
        this.Album.Delete();
} } } }

```

 Jest często bardziej użyteczne wyzwalacza przed usunięciem relacji od elementu roli, ponieważ to działa jednocześnie, gdy element zostanie usunięty, a po usunięciu samą relację. W przypadku relacji odwołania może być propagację usunięcia, gdy powiązany element zostanie usunięty, a nie samą relację zostanie usunięta. W tym przykładzie usuwa albumu podczas jego ostatniej wykonawcy uczestniczących zostanie usunięty, ale nie odpowiada, jeśli relacje są usuwane:

```
using System.Linq; ...
// Assumes a many-many reference relationship
// between Artist and Album.
partial class Artist
{
  protected override void OnDeleting()
  {
    base.OnDeleting();
    if (this.Store.InUndoRedoOrRollback) return;
    List<Album> toDelete = new List<Album>();
    foreach (Album album in this.Albums)
    {
      if (album.Artists.Where(artist => !artist.IsDeleting)
                        .Count() == 0)
      {
        toDelete.Add(album);
      }
    }
    foreach (Album album in toDelete)
    {
      album.Delete();
} } }

```

 Po wykonaniu <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> w elemencie OnDeleting i OnDeleted zostanie wywołana. Te metody są zawsze wykonywane wbudowanego - oznacza to, bezpośrednio przed i po usunięciu rzeczywistego. Jeśli Twój kod usuwa co najmniej dwa elementy, OnDeleting i OnDeleted zostanie wywołana w alternacyjne na wszystkich z nich z kolei.

##  <a name="rules"></a> Zasady usuwania i zdarzenia
 Alternatywą dla programów obsługi OnDelete można określić zasady usuwania i usuwania zdarzenia.

1.  **Usuwanie** i **usunąć** reguły są wyzwalane tylko w ramach transakcji, a nie w cofania lub ponownego wykonywania. Można ustawić je do kolejki do wykonania po zakończeniu transakcji, w którym odbywa się usuwanie. Usuwanie reguły są zawsze wykonywane przed żadnych reguł usunięte, które znajdują się w kolejce.

     Użyj reguł propagowanie zmian wpływających na tylko elementy w magazynie, w tym relacje, elementów diagramu i ich właściwości. Zazwyczaj reguły usunięcie służy do Propaguj usuwanie i regułą usuwania jest używany do tworzenia zastąpienia elementów i relacji.

     Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

2.  **Usunięte** magazynu zdarzenie jest wywoływane na końcu transakcji i jest wywoływana po wykonaniu cofania lub ponownego wykonywania. W związku z tym można propagację usunięcia obiektów poza magazynu, takich jak pliki, wpisów bazy danych lub innych obiektów w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     Aby uzyskać więcej informacji, zobacz [obsługi Propaguj zmiany poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).

    > [!WARNING]
    >  Po usunięciu elementu można uzyskać dostępu do jej wartości właściwości domeny, ale nie można nawigować łącza relacji. Jednak jeśli usunięto zdarzenie zostanie ustawiony na relacji, można także przejść dwa elementy, które były jego pełniących role. W związku z tym odpowiadanie na usunięcie elementu modelu, ale aby uzyskiwanie dostępu do elementu, do którego został połączony, ustawić zdarzenia delete relacji zamiast klasy domeny elementu modelu.

### <a name="example-deletion-rules"></a>Przykład usuwania reguł

```
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletingRule : DeletingRule
{
  public override void ElementDeleting(ElementDeletingEventArgs e)
  {
    base.ElementDeleting(e);
    // ...perform tasks to propagate imminent deletion
  }
}
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletedRule : DeleteRule
{
  public override void ElementDeleted(ElementDeletedEventArgs e)
  {
    base.ElementDeleted(e);
    // ...perform tasks such as creating new elements
  }
}

// The rule must be registered:
public partial class MusicLibDomainModel
{
  protected override Type[] GetCustomDomainModelTypes()
  {
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
    types.Add(typeof(AlbumDeletingRule));
    types.Add(typeof(AlbumDeletedRule));
    // If you add more rules, list them here.
    return types.ToArray();
  }
}

```

### <a name="example-deleted-event"></a>Przykład usunięto zdarzenie.

```
partial class NestedShapesSampleDocData
{
  protected override void OnDocumentLoaded(EventArgs e)
  {
    base.OnDocumentLoaded(e);
    DomainRelationshipInfo commentRelationship =
          this.Store.DomainDataDirectory
          .FindDomainRelationship(typeof(CommentsReferenceComponents));

    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));
  }

  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)
  {
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;
    Comment comment = link.Comment;
    Component component = link.Subject;
    if (comment.IsDeleted)
    {
      // The link was deleted because the comment was deleted.
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);
    }
    else
    {
      // It was just the link that was deleted - the comment itself remains.
      System.Windows.Forms.MessageBox.Show("Removed comment link to "
           + component.Name);
    }
  }
}

```

##  <a name="unmerge"></a> Rozdziel
 Operacja dołączony do elementu nadrzędnego elementu podrzędnego jest nazywana *scalania*. Występuje, gdy nowy element lub grupę elementów jest utworzony z przybornika, lub przeniesione z innej części modelu lub kopiowane ze Schowka. Oraz tworzenie osadzania relacji między nadrzędnym a jego nowy element podrzędny, operacji scalania można również skonfigurować dodatkowe relacje, tworzenie elementów pomocniczych i ustawiania wartości właściwości w elementach. Operacja scalania jest hermetyzowany w elemencie scalania — dyrektywa (EMD).

 EMD również hermetyzuje uzupełniające *Rozdziel* lub `MergeDisconnect` operacji. Jeśli masz klaster elementy zostały utworzone za pomocą scalania, zaleca się użyć skojarzonego Rozdziel można usunąć elementu z niego, jeśli chcesz pozostawić wszystkie pozostałe elementy w spójnym stanie. Operacja Rozdziel zazwyczaj będzie używać metod opisanych w poprzednich sekcjach.

 Aby uzyskać więcej informacji, zobacz [Dostosowywanie Element tworzenia i przepływu](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md)
- [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md)
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)