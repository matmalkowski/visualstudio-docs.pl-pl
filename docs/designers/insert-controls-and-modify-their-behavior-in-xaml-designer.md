---
title: Wstawianie kontrolek i modyfikowanie ich zachowania w programie Projektant XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: e2ec53e78bc88e18d9ba8e77aa888ffa855b64ea
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924158"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Wstawianie kontrolek i modyfikowanie ich zachowania w programie Projektant XAML

Formanty Zezwól użytkownikom na interakcję z aplikacją. Można ich użyć do zbierania informacji oraz do wykonywania działań takich jak animować obiektu lub zbadać źródło danych.

## <a name="add-controls-to-the-artboard"></a>Dodawanie formantów do obszaru roboczego

Można przeciągnij formanty z **zasoby** panelu na **kompozycji**, a następnie zmodyfikuj je w **właściwości** okna.

![Blend zasoby formanty kart](../designers/media/blend_assetsflipview_xaml.png)

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Formant poza obrazu, kształtu lub ścieżki

Można wprowadzić dowolny obiekt w formancie.

![Program Blend należy do kontrolki — okno dialogowe](../designers/media/blend_makeintocontrol_xaml.png)

Załóżmy na przykład obraz telewizji na środku strony. Można utworzyć kontrolki poza małe obrazy, które wyglądają jak przyciski telewizji. Następnie użytkownicy mogą kliknij tych przycisków, aby zmienić kanału.

Jest to możliwe, ponieważ przyciski są teraz kontrolki. Funkcje kontroli może odpowiedzieć interakcji użytkowników; w takim przypadku, gdy użytkownik kliknie przycisk.

Aby można było sterowania, wybierz obiekt. Następnie na **narzędzia** menu, kliknij przycisk **sterowania upewnij**.

## <a name="make-controls-do-things"></a>Zmień tryb formantów wykonywanie czynności

Formanty można wykonać akcje interakcji z użytkownikiem. Na przykład one można uruchomić animacji, aktualizowanie źródła danych lub odtwarzanie wideo.

Użyj *wyzwalaczy*, *zachowania*, i *zdarzenia* aby formanty wykonywanie czynności.

### <a name="triggers"></a>Wyzwalacze

A *wyzwalacza* zmiany właściwości lub wykonuje zadanie w odpowiedzi na zdarzenia lub zmiany w innej właściwości. Na przykład można zmienić kolor przycisku po umieszczeniu nad nim.

![Panel "Wyzwalaczy"](../designers/media/custom_button_blend_propertytriggerinfo.png)

### <a name="behaviors"></a>Zachowania

A *zachowanie* wielokrotnego użytku pakiet kodu. Go można zrobić coś więcej niż zmiany właściwości. Może wykonywać akcje, takie jak zapytania usługi danych. Blend jest dostarczany z małych kolekcji z nich, ale można dodać więcej. Przeciągnij zachowanie dowolnego obiektu w kompozycję, a następnie dostosować zachowanie przez ustawienie właściwości.

![Zachowanie FluidMoveBehavior w panelu Właściwości](../designers/media/b4_fluidmovebehaviorproperties_sample.png)

**Obejrzyj film:** ![ikona Play](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Blend porady: wprowadzenie do usługi za pomocą zachowań część 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Zdarzenia

Ultimate elastyczność obsługi *zdarzeń*. Będziesz mieć do pisania kodu.