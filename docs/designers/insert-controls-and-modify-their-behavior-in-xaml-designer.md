---
title: Wstawianie kontrolek i modyfikowanie ich zachowania w Projektancie XAML | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 09eb82bede66b839b7b3facdb61d8fc5d3ed2bd0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Wstawianie kontrolek i modyfikowanie ich zachowania w programie Projektant XAML
Formanty Zezwól użytkownikom na interakcję z aplikacją. Można ich użyć do zbierania informacji oraz do wykonywania działań takich jak animować obiektu lub zbadać źródło danych.  
  
 **W tym temacie:**  
  
-   [Dodawanie formantów do obszaru roboczego](#Insert)  
  
-   [Zmień tryb formantów wykonywanie czynności](#Modify)  
  
##  <a name="Insert"></a>Dodawanie formantów do obszaru roboczego  
 Można przeciągnij formanty z **zasoby** panelu na **kompozycji**, a następnie zmodyfikuj je w **właściwości** okna.  
  
 ![Program Blend &#45; Zasoby &#45; Właściwości FlipView](../designers/media/blend_assetsflipview_xaml.png "blend_AssetsFlipView_XAML")  
  
 Te pliki wideo pokazują, jak korzystać z niektórych formantów częściej.  
  
|Formant|Obejrzyj krótki klip wideo|  
|-------------|-------------------------|  
|`Menu`![ ] (../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Dodaj formanty](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|  
|`Button`![ ] (../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436b-b834-a91b7995a3ec")|![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [projektowania przycisku](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|  
|`Textblock`![ ] (../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-abcd-b0849edebada")|![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [dodać obrazy do blok tekstu](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|  
|`Slider`![ ] (../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815c-e98c930ac189")|![Konfigurowanie funkcji zainstalowanych](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [kompilacji suwak z etykietami](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|  
|`GridSplitter`![ ] (../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|![Konfigurowanie funkcji zainstalowanych](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracować z GridSplitter](http://msdn.microsoft.com/expression/cc188687.aspx)|  
  
### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Formant poza obrazu, kształtu lub ścieżki  
 Można wprowadzić dowolny obiekt w formancie.  
  
 ![Program Blend należy do kontrolki — okno dialogowe](../designers/media/blend_makeintocontrol_xaml.png "blend_MakeIntoControl_XAML")  
  
 Załóżmy na przykład obraz telewizji na środku strony. Można utworzyć kontrolki poza małe obrazy, które wyglądają jak przyciski telewizji. Następnie użytkownicy mogą kliknij tych przycisków, aby zmienić kanału.  
  
 Jest to możliwe, ponieważ przyciski są teraz kontrolki. Funkcje kontroli może odpowiedzieć interakcji użytkowników; w takim przypadku, gdy użytkownik kliknie przycisk.  
  
 Aby można było sterowania, wybierz obiekt. Następnie na **narzędzia** menu, kliknij przycisk **sterowania upewnij**.  
  
##  <a name="Modify"></a>Zmień tryb formantów wykonywanie czynności  
 Formanty można wykonać akcje interakcji z użytkownikiem. Na przykład one można uruchomić animacji, aktualizowanie źródła danych lub odtwarzanie wideo.  
  
 Użyj *wyzwalaczy*, *zachowania*, i *zdarzenia* aby formanty wykonywanie czynności.  
  
### <a name="triggers"></a>Wyzwalacze  
 A *wyzwalacza* zmiany właściwości lub wykonuje zadanie w odpowiedzi na zdarzenia lub zmiany w innej właściwości. Na przykład można zmienić kolor przycisku po umieszczeniu nad nim.  
  
 ![Panel "Wyzwalaczy"](../designers/media/custom_button_blend_propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [dodać wyzwalacza właściwości](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).  
  
### <a name="behaviors"></a>Zachowania  
 A *zachowanie* wielokrotnego użytku pakiet kodu. Go można zrobić coś więcej niż zmiany właściwości. Może wykonywać akcje, takie jak zapytania usługi danych. Blend jest dostarczany z małych kolekcji z nich, ale można dodać więcej. Przeciągnij zachowanie dowolnego obiektu w kompozycję, a następnie dostosować zachowanie przez ustawienie właściwości.  
  
 ![Zachowanie FluidMoveBehavior w panelu właściwości](../designers/media/b4_fluidmovebehaviorproperties_sample.png "b4_FluidMoveBehaviorProperties_Sample")  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Blend porady: wprowadzenie do usługi za pomocą zachowań część 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).  
  
### <a name="events"></a>Zdarzenia  
 Ultimate elastyczność obsługi *zdarzeń*. Będziesz mieć do pisania kodu.  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [dodać zdarzenia myszy](https://www.youtube.com/watch?v=2PMxAlb-x_E).