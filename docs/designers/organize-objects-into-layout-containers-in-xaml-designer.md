---
title: "Organizowanie obiektów w kontenery układów w Projektancie XAML | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 9c7b9c8f0f36435c2595a5df648daa54a614e278
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organizowanie obiektów w kontenery układów w projektancie XAML
Załóżmy, którym chcesz obiekty wyświetlane na stronach; obiekty, takie jak obrazy, przycisków i wideo. Może być mają pojawiać się w wiersze i kolumny, w jednym wierszu w pionie lub poziomie lub w stałego położenia.  
  
 Po już wcześniej szansy myśleć o wygląd strony, należy wybrać panelu układu. Wszystkie strony uruchomić jeden, ponieważ należy coś, aby dodać obiekty do. Domyślnie jest **siatki** , ale można zmienić.  
  
 Panele układu ułatwiają rozmieszczanie obiektów na stronie, ale ich nie więcej niż. One pomagają w projektowania dla różnych rozmiarów ekranu i rozwiązania. Gdy użytkownicy uruchomią aplikację, wszystko w panelu układu zmienia rozmiar odpowiadające nieruchomości ekranu urządzenia. Oczywiście jeśli nie chcesz, w tym układ, można zastąpić tego zachowania części układ lub całego układu. Przy użyciu właściwości height i width możesz kontrolować, które.  
  
 Ta strona opisuje panele układu i kontrolek, a następnie kieruje, do krótkich wideo, które ułatwiają rozpoczęciem pracy z nimi.  
  
> [!NOTE]
>  Niektóre pliki wideo mogą odwoływać się do mieszania lub Expression Blend, którego jako Visual Studio i Blend for Visual Studio za pomocą tego samego projektanta XAML.  
  
## <a name="layout-panels"></a>Panele układów  
 Uruchom ze strony, wybierając jedną z tych panele układu. Strony może mieć więcej niż jeden. Na przykład może być uruchamiany z **siatki** Układ panelu, a następnie dodaj **Panel stosu** do obszaru **siatki** , dzięki czemu można rozmieścić formanty w pionie w tym elemencie.  
  
 Poniższe panele układu są najbardziej popularly używane, ale istnieją inne. Można je znaleźć wszystkie w **zasoby** panelu.  
  
-   [Siatka](#Grid)  
  
-   [UniformGrid](#Uniform)  
  
-   [Kanwa](#Canvas)  
  
-   [StackPanel](#Stack)  
  
-   [WrapPanel](#Wrap)  
  
-   [DockPanel](#Dock)  
  
###  <a name="Grid"></a>Siatki  
 Rozmieść obiekty w wiersze i kolumny.  
  
 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441F-9136-98375fee87b7")  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [przy użyciu siatki](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
###  <a name="Uniform"></a>UniformGrid  
 Rozmieść obiekty w regionach równą lub jednolite, siatki. Panel ten program jest doskonały dla porządkowanie listy obrazów.  
  
 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")  
  
 (Dostępne tylko dla projektów WPF)  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Praca z UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
###  <a name="Canvas"></a>Kanwy  
 Rozmieść obiekty w dowolny sposób, który ma. Gdy użytkownicy uruchomią aplikację, te elementy zostaną stałej pozycji na ekranie.  
  
 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Praca z obszaru roboczego](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
###  <a name="Stack"></a>Panel stosu  
 Rozmieść obiekty w jednym wierszu poziomo czy pionowo.  
  
 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Praca z Panel stosu i WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Wrap"></a>WrapPanel  
 Rozmieść obiekty sekwencyjnie od lewej do prawej. Gdy panelu zabraknie miejsca na krawędzi prawej go *opakowuje* zawartość do następnego wiersza i tak dalej od lewej do prawej, góry do dołu. Można wprowadzić orientację panelu przewijania pionowego tak, aby obiekty przepływać z góry do dołu, od lewej do prawej.  
  
 (Dostępne tylko dla projektów WPF)  
  
 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Praca z Panel stosu i WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Dock"></a>DockPanel  
 Rozmieść obiekty, dzięki czemu te komputery pozostaną lub *dock*, do jednej krawędzi panelu.  
  
 (Dostępne tylko dla projektów WPF)  
  
 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## <a name="layout-controls"></a>Formanty układu  
 Można dodać obiekty do również formantów układu. Nie są one jako bogate jako panelu układu, ale mogą je znaleźć pomocne w niektórych scenariuszach.  
  
 Następujące opcje układu znajdują się najbardziej popularly używane, ale istnieją inne. Można je znaleźć wszystkie w **zasoby** panelu.  
  
-   [Obramowanie](#Border)  
  
-   [Popup](#Popup)  
  
-   [ScrollViewer](#Scroll)  
  
-   [UniformGrid](#Uniform)  
  
-   [Okno widoku](#View)  
  
###  <a name="Border"></a>Obramowania  
 Utwórz obramowanie, tło lub oba elementy wokół obiektu. Można dodać tylko jeden obiekt do **obramowania**. Jeśli chcesz zastosować obramowania i tło więcej niż jeden obiekt, należy dodać panelu układu **obramowania**. Następnie należy dodać obiekty do tego panelu lub formantu.  
  
 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-bbc4-57538b8289ff")  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Praca z obramowania](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
###  <a name="Popup"></a>Menu podręczne  
 Pokaż informacje i opcje dla użytkowników w oknie. Można dodać tylko jeden obiekt do **podręcznego**. Domyślnie **podręcznego** zawiera **siatki** , ale można zmienić.  
  
###  <a name="Scroll"></a>ScrollViewer  
 Włącz używa do przewiń w dół strony lub części strony. Można dodać tylko jeden obiekt do **ScrollViewer** , ułatwia dużo znaczeniu, takie jak dodać panelu układu **siatki** lub **Panel stosu**.  
  
 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")  
  
###  <a name="View"></a>Viewbox  
 Skalowanie obiektów, podobnie jak w przypadku czy z formantem powiększenia. Można dodać tylko jeden obiekt do **Viewbox**. Jeśli chcesz zastosować ten efekt do więcej niż jeden obiekt, należy dodać panelu układu, aby **ViewBox**, a następnie dodaj formanty do panelu układu.  
  
 (Dostępne tylko dla projektów WPF)  
  
 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md)   
 [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)