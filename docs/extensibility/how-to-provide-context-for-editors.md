---
title: 'Porady: Podaj kontekstu edytory | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d9b89c4e45f8268df55386d321816325fb50174c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-context-for-editors"></a>Porady: Podaj kontekstu edytorów
Edytora kontekstu jest aktywny tylko wtedy, gdy Edytor ma fokus lub był aktywny bezpośrednio przed fokus została przeniesiona do okna narzędzia. Kontekst dla edytora zapewniają w następujący sposób:  
  
1.  Utwórz pakiet z kontekstu.  
  
2.  Opublikuj zbiorze kontekstu identyfikator elementu zaznaczenia (SEID).  
  
3.  Obsługa kontekstu w zbiorze.  
  
 Zadania te są objęte poniższych procedur. Aby uzyskać więcej informacji na temat podawania kontekstu, zobacz **Programowanie niezawodnych** dalszej części tego tematu.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Aby utworzyć zbiór kontekst dla edytora lub projektanta  
  
1.  Wywołanie `QueryService` na Twojej <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfejs na potrzeby <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> usługi.  
  
     Wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> interfejsu, jest zwracany.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> metodę, aby utworzyć nowy zbiór kontekstu lub kontekst podrzędny.  
  
     Wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> interfejsu, jest zwracany.  
  
3.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> metodę, aby dodać atrybuty, słowa kluczowe wyszukiwania lub słów kluczowych F1 do zbioru kontekstu lub kontekst podrzędny.  
  
4.  Jeśli tworzysz zbiór kontekst podrzędny wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> metodę, aby połączyć zbiorze kontekst podrzędny zbiorze kontekst nadrzędnego.  
  
5.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> aby otrzymać powiadomienie po **Pomoc dynamiczna** okno jest aktualizacja.  
  
     O **Pomoc dynamiczna** edytora Wywołaj okno Jeśli jest gotowy do aktualizacji daje możliwość opóźnienie zmiana kontekstu, dopóki nie wystąpi aktualizacji. W ten sposób można zwiększyć wydajność, ponieważ umożliwia opóźnienie systemem algorytmów dużo czasu do czasu bezczynności systemu.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Aby opublikować zbiorze kontekstu SEID  
  
1.  Wywołanie `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> zwracanej wskaźnik do usługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfejsu.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, określając identyfikator elementu (`elementid` parametru) wartość SEID_UserContext, aby wskazać, czy kontekst jest przekazywany na poziomie globalnym.  
  
3.  Jeśli Edytor lub designer staje się aktywny, wartości w jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> obiektu są propagowane do globalnego zaznaczenia. Konieczne jest ukończenie tego procesu na początku sesji, a następnie umieść wskaźnik do kontekście globalnym utworzony podczas wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
### <a name="to-maintain-the-context-bag"></a>Aby zachować zbiorze kontekstu  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> do upewnij się, że **Pomoc dynamiczna** wywołuje okno edytora lub projektanta przed jego aktualizacji.  
  
     Dla każdego zbioru kontekstu, który wywołał <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> po zbiorze kontekstu jest tworzony i zaimplementowała <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> powiadomiono dostawca kontekstu zostanie zaktualizowany pakiet kontekstu. To wywołanie służy do zmiany atrybutów i słowa kluczowe w zbiorze kontekstu i w dowolnym torbach kontekst podrzędny przed **Pomoc dynamiczna** występuje usługi Windows update.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> w zbiorze kontekstu, aby wskazać, że edytor lub projektanta ma nowy kontekst.  
  
     Gdy **Pomoc dynamiczna** wywołań okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> aby wskazać, że aktualizacji, Edytor lub projektanta można aktualizować kontekstu odpowiednio dla zbioru kontekst nadrzędnego i wszelkie torebki kontekst podrzędny o tej godzinie.  
  
    > [!NOTE]
    >  `SetDirty` Automatycznie ustawiono flagę `true` zawsze, gdy kontekst jest dodane lub usunięte z zbiorze kontekstu. **Pomoc dynamiczna** tylko wywołuje okno <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> w zbiorze kontekstu Jeśli `SetDirty` flaga jest ustawiona na `true`. Jest resetowany do `false` po aktualizacji.  
  
3.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> można dodać kontekstu do kolekcji active kontekstu lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> usunąć kontekstu.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Podczas pisania własnych edytora, należy wykonać wszystkie trzy procedury w tym temacie, aby zapewnić kontekstu edytora.  
  
> [!NOTE]
>  Poprawnie uaktywnić okna edytora lub projektanta i upewnij się, że routing poleceń jest zaktualizowane prawidłowo, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> dla składnika, aby stał się okna posiadającego fokus.  
  
 SEID to zbiór właściwości, które zmieniają się na podstawie zaznaczenia. SEID informacje są dostępne za pośrednictwem globalnej zaznaczenia. Globalne zaznaczenie jest podłączona do zdarzenia wyzwolone przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfejsu, i zawiera listę wszystkich elementów, która jest zaznaczony (bieżącego edytora, bieżące okno narzędzia bieżącej hierarchii i tak dalej).  
  
 Edytory i projektantów w którego kontekście można zmienić po każdej zmianie kursor zostanie wyrazu, jest nieefektywne stale aktualizacji zbioru kontekstu. Aby aktualizowanie efektywniejsze kiedykolwiek wykryć kursora przenoszenie w edytorze lub okna projektanta, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. W ten sposób służy do przechowywania zmiany kontekstu czas bezczynności i Usługa kontekstu IDE wysyła powiadomienie do edytora lub projektanta który **Pomoc dynamiczna** okna jest aktualizowana. Takie podejście jest używany w procedurze "Aby obsługa zbiorze kontekstu" w tym temacie.  
  
 Po podaniu kontekstu dla działania w edytorze lub projektanta, należy podać określone słowo kluczowe F1, aby użytkownicy mogli uzyskać pomoc dotyczącą edytora lub projektanta sam.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>