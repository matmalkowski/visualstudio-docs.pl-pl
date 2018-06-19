---
title: Lista zdarzeń grafiki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3640a1bbb06de7b05eeb62f847504690921b324
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477839"
---
# <a name="graphics-event-list"></a>Lista zdarzeń grafiki
Użyj listy zdarzeń grafiki w analizatora grafiki programu Visual Studio do eksplorowania zdarzenia Direct3D, które zostały zarejestrowane podczas renderowania ramka gry lub aplikacji.  
  
 Jest to lista zdarzeń:  
  
 ![Lista zdarzeń, które mają "Index" w nazwie. ] (media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")  
  
## <a name="using-the-event-list"></a>Korzystanie z listy zdarzeń  
 Po wybraniu zdarzenia w przypadku listy, jego ma odzwierciedlone w informacje, które jest wyświetlane przez inne narzędzia analizy grafiki; za pomocą listy zdarzeń w połączeniu z innych narzędzi należy zbadać problem z renderowaniem szczegółowo w celu ustalenia jego przyczyny. Aby dowiedzieć się więcej na temat jak rozwiązać problemy z renderowaniem, używając listy zdarzeń razem z innymi narzędziami analizy grafiki, zobacz [przykłady](graphics-diagnostics-examples.md).  
  
 Przy użyciu funkcji listy zdarzeń skutecznie jest ważne dla poruszania się złożonych ramek, które mogą zawierać tysiące zdarzenia. Aby efektywnie korzystać z listy zdarzeń, wybierz widok działa najlepiej, można użyć wyszukiwania, aby filtrować listę zdarzeń, skorzystaj z linków, aby dowiedzieć się więcej o obiektach Direct3D, które są skojarzone ze zdarzeniem i użyj strzałki przycisków, aby przechodzić między narysuj wywołania szybko.  
  
### <a name="color-coded-events-in-direct3d-12"></a>Oznaczone kolorami zdarzeń w Direct3D 12  
 Direct3D 12 udostępnia wiele kolejek, które odpowiadają funkcje sprzętowe. Aby ułatwić identyfikację kolejki, skojarzone ze zdarzeniem określonego grafiki w Direct3D 12, zdarzenia są oznaczone kolorami na liście zdarzeń zgodnie z ich kolejki podczas pracy z funkcją przechwytywania aplikacji Direct3D 12.  
  
|Direct3D 12 kolejki|Kolor|  
|-----------------------|-----------|  
|Renderowanie kolejki|zielony|  
|Obliczenia bazy danych kolejki|żółty|  
|Skopiuj kolejki|kolor pomarańczowy|  
  
 Direct3D 11 nie uwidacznia wielu kolejek, więc zdarzenia nie są oznaczone kolorami listy zdarzeń podczas pracy z funkcją przechwytywania aplikacji Direct3D 11.  
  
### <a name="event-list-views"></a>Widoki list zdarzeń  
 Na liście zdarzeń obsługuje dwa różne widoki, które organizowanie zdarzeń grafiki na różne sposoby do obsługi przepływu pracy, a preferencje. Pierwszy widok jest *GPU działać widoku* który organizuje zdarzeń i ich stan skojarzony hierarchicznie. Drugi widok *widoku osi czasu* zdarzenia które organizuje w porządku chronologicznym, jako płaską listę.  
  
 **Działanie procesora GPU** widoku  
 Wyświetla przechwycić zdarzeń i ich stan w hierarchii. Zdarzenia, takie jak wywołania rysowania, czyści obecna i części dotyczącej widoków składają się najwyższego poziomu hierarchii. W przypadku listy, możesz rozszerzyć wywołań rysowania kierowanych do wyświetlenia stanu urządzenia, które były aktualne w momencie wywołania rysunku; i każdego rodzaju stanu, aby wyświetlić zdarzenia, które ustawienia ich wartości można rozwinąć. Na tym poziomie można również sprawdzić czy w określonym stanie została ustawiona w poprzedniej ramki, czy została ustawiona więcej niż raz od czasu ostatniego rysowania wywołania.  
  
 **Osi czasu** widoku  
 Wyświetla poszczególnych zdarzeń przechwyconych w kolejności chronologicznej. Ten sposób organizowania listy zdarzeń jest taka sama, jak w poprzednich wersjach programu Visual Studio.  
  
##### <a name="to-change-the-event-list-view-mode"></a>Aby zmienić tryb widoku listy zdarzeń  
  
-   W **listy zdarzeń grafiki** okna powyżej listę zdarzeń, zlokalizuj **widoku** listy rozwijanej i wybierz opcję **osi czasu** widoku lub **działanie procesora GPU** widoku.  
  
### <a name="filtering-events"></a>Filtrowanie zdarzeń  
 Można użyć pola wyszukiwania — znajdujący się w prawym górnym rogu **listy zdarzeń grafiki** okna — Aby filtrować listę zdarzenia, aby uwzględnić tylko zdarzenia, których nazwy zawierają określonych słów kluczowych. Możesz określić pojedynczy słów kluczowych, takich jak `Vertex`— jak pokazano na poprzedniej ilustracji — lub wiele słów kluczowych przy użyciu rozdzielaną średnikami listę takich jak `Draw;Primitive`— zgodnej zdarzenia, które albo `Draw` lub `Primitive` w nazwach. Wyszukiwania są wrażliwe na odstępu — na przykład `VSSet` i `VS Set` są różne wyszukiwania — tak upewnij się, że wyszukiwanie formularza dokładnie.  
  
### <a name="moving-between-draw-calls"></a>Przenoszenie między wywołań rysowania  
 Ponieważ badanie `Draw` wywołania jest szczególnie ważne, można użyć **wywołanie rysowania przejdź do następnego** i **wywołanie rysowania przejdź do poprzedniej** przyciski — znajdujący się w lewym górnym rogu **Lista zdarzeń grafiki** okna, aby znaleźć i szybkie przenoszenie między wywołań rysowania.  
  
### <a name="links-to-graphics-objects"></a>Łącza do obiektów graficznych  
 Aby poznać określonych zdarzeń grafiki, może być konieczne dodatkowe informacje o bieżącym stanie Direct3D lub Direct3D obiekty, które odwołują się zdarzenia. Wiele zdarzeń zawierają łącza do tych informacji, które możesz wykonać, aby uzyskać więcej szczegółów.  
  
## <a name="kinds-of-events-and-event-markers"></a>Rodzaje zdarzeń i znaczników zdarzeń  
 Zdarzenia, które są wyświetlane w przypadku listy są pogrupowane w kategorie cztery: Ogólne zdarzenia rysowania zdarzeń, liczba grup zdarzeń zdefiniowanych przez użytkownika i znaczników zdarzeń zdefiniowanych przez użytkownika. Z wyjątkiem zdarzenia ogólne każde zdarzenie zostanie wyświetlona oraz ikonę, która wskazuje należącego do kategorii.  
  
|Ikona|Opis zdarzenia|  
|----------|-----------------------|  
|(Brak ikony)|Zdarzenia ogólne<br /> Wszystkie zdarzenia, które nie jest zdarzeń zdefiniowanych przez użytkownika, grupy zdarzeń zdefiniowanych przez użytkownika lub rysowania zdarzeń.|  
|![Ikona zdarzenia rysowania](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Zdarzenie rysowania<br /> Oznacza zdarzenie rysowania, który wystąpił podczas przechwyconej ramce.|  
|![Użytkownik&#45;zdefiniowane Ikona znacznika zdarzenia](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Grupa zdarzeń zdefiniowanych przez użytkownika<br /> Grupuje pokrewne zdarzenia, zgodnie z definicją w aplikacji.|  
|![Użytkownik&#45;zdefiniowane Ikona znacznika zdarzenia](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Znacznik zdarzeń zdefiniowanych przez użytkownika<br /> Oznacza określonej lokalizacji, zgodnie z definicją w aplikacji.|  
  
## <a name="marking-user-defined-events-in-your-app"></a>Oznaczanie zdarzeń zdefiniowanych przez użytkownika w aplikacji  
 Zdarzenia zdefiniowane przez użytkownika są specyficzne dla aplikacji. Można używać ich do skorelowania istotnych zdarzeń występujących w aplikacji ze zdarzeniami w listy zdarzeń grafiki. Na przykład można utworzyć zdarzenia zdefiniowane przez użytkownika grup w celu zorganizowania zdarzenia powiązane — takich jak te, które renderują interfejsu użytkownika — na grupy i hierarchie są tak, aby łatwiej przeglądać listę zdarzeń, lub można utworzyć znaczniki, gdy niektóre rodzaje obiektów rysowane, dzięki czemu można łatwo znaleźć listy zdarzeń grafiki wydarzenia.  
  
 Aby utworzyć grupy i znaczniki w aplikacji, należy użyć tych samych interfejsów API Direct3D udostępniający do użytku przez inne Direct3D narzędzia debugowania. Te interfejsy API czasami zmieniać między wersjami programu Direct3D, ale podstawowe funkcje jest taka sama.  
  
### <a name="user-defined-events-in-direct3d-12"></a>Zdarzenia zdefiniowane przez użytkownika w Direct3D 12  
 Aby utworzyć grupy i znaczniki w Direct3D 12, przy użyciu interfejsów API opisanego w tej sekcji. Poniższa tabela zawiera podsumowanie interfejsów API, które można użyć w zależności od tego, czy są oznaczenie zdarzeń w kolejce polecenia lub poleceń listy.  
  
|Opis interfejsu API|[ID3D12CommandQueue](https://msdn.microsoft.com/library/dn788627.aspx)|[ID3D12GraphicsCommandList](https://msdn.microsoft.com/library/dn903537.aspx)|  
|---------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Sprawdź dostępność zdarzeń zdefiniowanych przez użytkownika|[PIXGetStatus](http://msdn.microsoft.com/en-us/f7ebd985-fb5d-46d7-abec-099df4b9be0e)|[PIXGetStatus](http://msdn.microsoft.com/en-us/1046ac43-a0a3-42bf-bae8-14aa72fa7567)|  
|Rozpocznij grupy zdarzeń|[PIXBeginEvent](http://msdn.microsoft.com/en-us/5f51fff7-f313-4558-965b-2a443653cd7b)|[PIXBeginEvent](http://msdn.microsoft.com/en-us/4ddb3311-b9b5-449a-bbfb-7634e0d56e87)|  
|W końcu grupy zdarzeń|[PIXEndEvent](http://msdn.microsoft.com/en-us/fb526bf2-c17d-4a2a-8665-3b577a0f7fba)|[PIXEndEvent](http://msdn.microsoft.com/en-us/a3cd34a9-9dd9-40e1-ae86-0214b25ff185)|  
|Tworzenie znacznika zdarzenia|[PIXSetMarker](http://msdn.microsoft.com/en-us/0caf49ed-c99d-405e-89f4-0c887b8474ad)|[PIXSetMarker](http://msdn.microsoft.com/en-us/6610e5b9-a0c5-4236-b551-b6eb9fac64c1)|  
  
### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Zdarzenia zdefiniowane przez użytkownika programu Direct3D 11 i starszych wersji  
 Tworzenie grup i znaczniki programu Direct3D 11 lub wcześniej, przy użyciu interfejsów API opisanego w tej sekcji. Poniższa tabela zawiera podsumowanie interfejsów API, które służy do różnych wersji programu Direct3D 11 i wcześniejszych wersjach programu Direct3D.  
  
|Opis interfejsu API|[ID3D11DeviceContext2](http://msdn.microsoft.com/library/windows/desktop/dn280498.aspx) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](http://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11.1)|Rodzina D3DPerf_ interfejsu API (Direct3D 11.0 i starsze)|  
|---------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------|  
|Rozpocznij grupy zdarzeń|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|  
|W końcu grupy zdarzeń|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|  
|Tworzenie znacznika zdarzenia|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|  
  
 Można użyć dowolnego z tych interfejsów API, które obsługuje używanej wersji programu Direct3D — na przykład, jeśli ma być przeznaczona dla interfejsu API programu Direct3D 11.1, można albo `SetMarker` lub `D3DPerf_SetMarker` można utworzyć znacznik zdarzeń, ale nie `SetMarkerInt` ponieważ jego dostępne tylko w Direct3D 11.2 — a nawet można łączyć ze sobą obsługują różne wersje programu Direct3D w tej samej aplikacji.  

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## Zawiera zasób historii Visual Studio 2017 i większa **historii zasobów** okna.  Wybieranie ikona monitorowania ![ikona monitorowania](media/gfx_watch.png) obok wpisu w **listy zdarzeń** powoduje wyświetlenie okna **historii zasobów** okna pokazano poniżej:

![Historia zasobów](media/gfx_diag_resource_history.png)

To okno umożliwia wyświetlenie historii wybrany element na liście zdarzeń.  U góry listy rozwijanej można wybrać inne elementy, aby wyświetlić historię.  W górnej połowie okna zawiera **zdarzeń Instalatora ramki**.  Są to zdarzenia, które można podzielić na *Utwórz* wpisz kategorię i wywołań, które zwykle inicjowania i utworzenia zasobu.  Dolnej połowie okna zawiera **zdarzenia ramki** sekcji.  Służą one do normalnej odczytu i zapisu zdarzeń występujących podczas użycia zasobu.  

Kolumny|Opis
---|---
**Typ** | Zawiera typ wpisu, zwykle *Utwórz*, *odczytu* i *zapisu*.  
**Widok** | Pokazuje miniatur zasobu w tej chwili.  Dwukrotnie kliknij miniaturę, aby otworzyć widok szczegółów zasobów w tym czasie.  
**Event**| Pokazuje wywołanie metody wystąpienia, który wygenerował zdarzenie.  Wszelkie dodatkowe historii na poszczególne elementy można wyświetlić, wybierając ikonę czujki ![ikona monitorowania](media/gfx_watch.png) odpowiednie wiersza.  Ponadto dowolny element, który jest rysowana na niebiesko, takich jak `m_commandList` na zrzucie ekranu powyżej, można wybrać więcej szczegółów.
<!-- /VERSIONLESS -->

## <a name="see-also"></a>Zobacz też  
 [Przewodnik: brak obiektów spowodowany stanem urządzenia](walkthrough-missing-objects-due-to-device-state.md)