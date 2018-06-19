---
title: Organizowanie obiektów w kontenery układów w projektancie XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 2da34d180a59212b171e484129df27d94f580a1a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924547"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organizowanie obiektów w kontenery układów w projektancie XAML

W tym artykule opisano panele układu i formantów w Projektancie XAML.

Załóżmy, którym chcesz obiekty wyświetlane na stronach; obiekty, takie jak obrazy, przycisków i wideo. Może być mają pojawiać się w wiersze i kolumny, w jednym wierszu w pionie lub poziomie lub w stałego położenia.

Po już wcześniej szansy myśleć o wygląd strony, należy wybrać panelu układu. Wszystkie strony uruchomić jeden, ponieważ należy coś, aby dodać obiekty do. Domyślnie jest **siatki**, ale można zmienić.

Panele układu ułatwiają rozmieszczanie obiektów na stronie, ale ich nie więcej niż. One pomagają w projektowania dla różnych rozmiarów ekranu i rozwiązania. Gdy użytkownicy uruchomią aplikację, wszystko w panelu układu zmienia rozmiar odpowiadające nieruchomości ekranu urządzenia. Oczywiście jeśli nie chcesz, w tym układ, można zastąpić tego zachowania części układ lub całego układu. Przy użyciu właściwości height i width możesz kontrolować, które.

## <a name="layout-panels"></a>Panele układów

Uruchom ze strony, wybierając jedną z tych panele układu. Strony może mieć więcej niż jeden. Na przykład może być uruchamiany z **siatki** Układ panelu, a następnie dodaj **Panel stosu** do obszaru **siatki** , dzięki czemu można rozmieścić formanty w pionie w tym elemencie.

Poniższe panele układu są najbardziej popularly używane, ale istnieją inne. Można je znaleźć wszystkie w **zasoby** panelu.

- [Siatka](#Grid)

- [UniformGrid](#UniformGrid)

- [Kanwa](#Canvas)

- [StackPanel](#stackpanel)

- [WrapPanel](#wrappanel)

- [DockPanel](#dockpanel)

### <a name="grid"></a>Siatka

Rozmieść obiekty w wiersze i kolumny.

![Panelu układu siatki](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>UniformGrid

Rozmieść obiekty w regionach równą lub jednolite, siatki. Panel ten program jest doskonały dla porządkowanie listy obrazów.

![UniformGrid panelu układu](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

(Dostępne tylko dla projektów WPF).

### <a name="canvas"></a>Kanwa

Rozmieść obiekty w dowolny sposób, który ma. Gdy użytkownicy uruchomią aplikację, te elementy zostaną stałej pozycji na ekranie.

![Panelu układu kanwy](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

Rozmieść obiekty w jednym wierszu poziomo czy pionowo.

![Panel stosu panelu układu](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

Rozmieść obiekty sekwencyjnie od lewej do prawej. Gdy panelu zabraknie miejsca na krawędzi prawej go *opakowuje* zawartość do następnego wiersza i tak dalej od lewej do prawej, góry do dołu. Można wprowadzić orientację panelu przewijania pionowego tak, aby obiekty przepływać z góry do dołu, od lewej do prawej.

(Dostępne tylko dla projektów WPF).

![WrapPanel panelu układu](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

Rozmieść obiekty, dzięki czemu te komputery pozostaną lub *dock*, do jednej krawędzi panelu.

(Dostępne tylko dla projektów WPF).

![DockPanel panelu układu](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**Obejrzyj krótki klip wideo:** ![przycisk Odtwórz](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Formanty układu

Można dodać obiekty do również formantów układu. Nie są one jako bogate jako panelu układu, ale mogą je znaleźć pomocne w niektórych scenariuszach.

Następujące opcje układu znajdują się największą popularnością, ale istnieją inne. Można je znaleźć wszystkie w **zasoby** panelu.

- [Obramowanie](#Border)

- [Popup](#Popup)

- [ScrollViewer](#scrollviewer)

- [Okno widoku](#viewbox)

### <a name="border"></a>Obramowanie

Utwórz obramowanie, tło lub oba elementy wokół obiektu. Można dodać tylko jeden obiekt do **obramowania**. Jeśli chcesz zastosować obramowania i tło więcej niż jeden obiekt, należy dodać panelu układu **obramowania**. Następnie należy dodać obiekty do tego panelu lub formantu.

![Formant układu obramowania](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>Okno podręczne

Pokaż informacje i opcje dla użytkowników w oknie. Można dodać tylko jeden obiekt do **podręcznego**. Domyślnie **podręcznego** zawiera **siatki** , ale można zmienić.

### <a name="scrollviewer"></a>ScrollViewer

Włącz używa do przewiń w dół strony lub części strony. Można dodać tylko jeden obiekt do **ScrollViewer** , ułatwia dużo znaczeniu, takie jak dodać panelu układu **siatki** lub **Panel stosu**.

![Kontrolki ScrollViewer układu](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Okno widoku

Skalowanie obiektów, podobnie jak w przypadku czy z formantem powiększenia. Można dodać tylko jeden obiekt do **Viewbox**. Jeśli chcesz zastosować ten efekt do więcej niż jeden obiekt, należy dodać panelu układu, aby **ViewBox**, a następnie dodaj formanty do panelu układu.

(Dostępne tylko dla projektów WPF).

![Formant układu ViewBox](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>Zobacz także

- [Praca z elementami w projektancie XAML](../designers/working-with-elements-in-xaml-designer.md)
- [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)