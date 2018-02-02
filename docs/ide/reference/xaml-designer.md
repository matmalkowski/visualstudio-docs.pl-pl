---
title: Strona opcji Projektant XAML | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- uwp
ms.openlocfilehash: bf71bb6f2d52159ab203d14c690a73525af091ae
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="xaml-designer-options-page"></a>Strona opcji projektanta XAML

Użyj **projektanta XAML** Strona opcji, aby określić sposób formatowania elementów i atrybutów w dokumencie XAML. Aby otworzyć tę stronę, wybierz **narzędzia** menu, a następnie wybierz **opcje**. Aby uzyskać dostęp do **projektanta XAML** właściwości wybierz pozycję **projektanta XAML** węzła. Ustawienia projektanta XAML zostaną zastosowane po otwarciu dokumentu. Tak Jeśli wprowadzisz zmiany w ustawieniach, musisz zamknąć i ponownie otworzyć Visual Studio, aby zobaczyć zmiany.

> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  

## <a name="enable-xaml-designer"></a>Włącz projektanta XAML
Po wybraniu tego ustawienia umożliwia projektanta XAML. Projektant XAML zawiera obszar roboczy visual do edycji dokumentów XAML. Niektóre funkcje programu Visual Studio, takie jak IntelliSense zasobów lub powiązań danych, wymagają włączenia projektanta XAML.

Następujące ustawienia mają zastosowanie tylko wtedy, gdy jest włączona projektanta XAML. Jeśli zmienisz tę opcję, będzie konieczne ponowne uruchomienie programu Visual Studio dla ustawienia zaczęły obowiązywać.

## <a name="default-document-view"></a>Widok domyślny dokument
Użyj tego ustawienia do formantu, czy widok projektu jest wyświetlany, gdy załadowano dokumenty XAML.

|||  
|-|-|  
|**Wyświetl źródło**|Określa, czy tylko źródła XAML jest wyświetlana w widoku XAML. Jest to przydatne podczas ładowania dużych dokumentów.|  
|**Widok projektu**|Określa, czy tylko element wizualny projektanta XAML jest wyświetlana w widoku XAML.|  
|**Widok podzielony**|Określa, czy zarówno projektanta XAML i źródła XAML są wyświetlane obok siebie w widoku XAML (na podstawie lokalizacji **orientacji podziału** ustawienie).|  

## <a name="split-orientation"></a>Orientacja podziału
To ustawienie służy do kontrolowania, kiedy i jak projektanta XAML jest wyświetlana podczas edytowania dokumentu XAML. Te ustawienia mają zastosowanie tylko wtedy, gdy **domyślny widok dokumentu** ustawiono **podzielony widok**.

|||  
|-|-|  
|**Pionowe**|Źródło XAML jest wyświetlana po lewej stronie widoku XAML, a po drugiej stronie zostanie wyświetlona projektanta XAML.|  
|**Poziomy**|Projektant XAML jest wyświetlana w górnej części widoku XAML i źródła XAML jest wyświetlana poniżej.|  
|**Default**|Dokument XAML używa orientację podziału zalecane dla platformy docelowej projektu dokumentu. Dla większości platform, co jest równoważne **poziome**.|  

## <a name="zoom-by-using"></a>Powiększenie przy użyciu
Użyj tego ustawienia, aby określić, jak powiększenia działa podczas edytowania dokumentu XAML.

|||  
|-|-|  
|**Kółka myszy**|Przewijanie kółko myszy, aby powiększyć w Projektancie XAML.|  
|**CTRL + kółka myszy**|Powiększenie w Projektancie XAML, naciskając klawisz CTRL podczas przewijania kółka myszy.|  
|**ALT + myszy koło**|Powiększenie w Projektancie XAML, naciskając klawisz ALT podczas przewijania kółka myszy.|  

Te ustawienia określają zachowanie projektanta podczas edytowania dokumentu XAML.

|||  
|-|-|  
|**Automatycznie nazwij elementy interakcyjne przy tworzeniu**|Określa, czy nazwa domyślna jest dostarczany dla nowego elementu interaktywne, dodając je do projektanta.|  
|**Automatyczne wstawianie właściwości układu po utworzeniu elementu**|Określa, czy właściwości układu są udostępniane dla nowego elementu, dodając je do projektanta.|  
|**Wiązania kwadrantu na podstawie układu**|Określa, czy aktualnie wybrany formant jest wyrównywany do najbliższej krawędziami kontenera nadrzędnego. Jeśli to pole wyboru jest wyczyszczone, wyrównanie formantu nie zmieniać podczas przenoszenia lub operacji tworzenia.|  
|**Automatycznie wypełnij elementy przybornika**|Określa, czy kontrolek użytkownika i kontrolek niestandardowych w bieżącym rozwiązaniu są wyświetlane w przyborniku automatycznie.|  

## <a name="settings-blend-only"></a>Ustawienia (tylko w programie Blend)
Te opcje umożliwiają określenie ustawień podczas edytowania plików XAML przy użyciu programu Blend.

|||  
|-|-|  
|**Powiększenie przy użyciu**|Powiększenie w Projektancie XAML przewijając kółka myszy lub naciskając klawisz CTRL lub ALT podczas przewijania kółka myszy.|  
|**Typ jednostki**|Określa, czy pomiarów w Projektancie są oparte na punktach lub pikselach. Ponieważ uniwersalnych aplikacji systemu Windows nie obsługują punkty, jednostki są automatycznie konwertowane na następującą liczbę pikseli, jeśli **punktów** jest zaznaczone.|  

## <a name="artboard-blend-only"></a>Obszar roboczy (tylko w programie Blend)
Użyj tych ustawień, aby określić zachowanie projektanta XAML podczas edytowania dokumentów XAML w Blend.

### <a name="snapping"></a>Przyciągania

|||  
|-|-|  
|**Pokaż siatkę przyciągania**|Gdy ta opcja jest zaznaczona, linie siatki są wyświetlane w projektancie, aby ułatwić wyrównywanie formantów. Formanty dodane do projektanta przyciąganie do linie siatki podczas **przyciąganie do linii siatki** opcja jest zaznaczona.|  
|**Przyciąganie do linii siatki**|Podczas dodawania lub przemieszczania wokół projektanta formantów, przyciąganie do linii siatki.|  
|**Odstępy siatki**|Określa odstępy między liniami siatki w pikselach lub punktów (zgodnie z ustaleniami **typu jednostki** ustawienie).|  
|**Przyciąganie do linii wyrównania**|Określa, czy formanty przyciąganie do linii wyrównania.|  
|**Domyślny margines**|Gdy **przyciąganie do linii wyrównania** jest włączone, określa odstępy między formantem a linie przyciągania w pikselach lub punktów (zgodnie z ustaleniami **typu jednostki** ustawienie).|  
|**Domyślna uzupełniania**|Gdy **przyciąganie do linii wyrównania** jest włączone, określa dodatkowy odstęp między formantem a linie przyciągania w pikselach lub punkty (zgodnie z ustaleniami **typu jednostki** ustawienie).|  

### <a name="animation"></a>Animacja
To ustawienie służy do określenia, czy pojawi się ostrzeżenie podczas zależne (bez przyspieszania) w programie Blend włączone są animacje.

### <a name="effects"></a>Efekty
Użyj tych ustawień, aby określić, czy efekty mają być renderowane podczas edycji XAML plików w Projektancie XAML przy użyciu programu Blend.

|||  
|-|-|  
|**Renderowanie efektów**|Określa, czy efekty renderować podczas edytowania plików XAML w Projektancie XAML przy użyciu programu Blend.|  
|**Próg powiększenia**|Określa procent powiększenia w których efekty renderowania, kiedy **Renderowanie efektów** pole wyboru jest zaznaczone. Jeśli powiększenie poza to ustawienie efekty już renderować w Projektancie XAML.|  

## <a name="see-also"></a>Zobacz także

[XAML w WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)  
[Przewodnik: moja pierwsza aplikacja klasyczna WPF](../../designers/walkthrough-my-first-wpf-desktop-application2.md)
