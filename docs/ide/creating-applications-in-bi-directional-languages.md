---
title: "Tworzenie aplikacji w językach dwukierunkowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: db7afbc68ab4e02803959dd0ff0b4de92233fece
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-applications-in-bi-directional-languages"></a>Tworzenie aplikacji w językach dwukierunkowych
Visual Studio umożliwia tworzenie aplikacji, które umożliwia poprawne wyświetlanie tekstu w językach zapisywane prawej do lewej, m.in. arabski i hebrajski. W przypadku niektórych funkcji po prostu można ustawić właściwości. W pozostałych przypadkach musi implementować funkcje w kodzie.  
  
> [!NOTE]
>  Aby wprowadzić i wyświetlić języki dwukierunkowe, musi działać z wersją systemu Windows, która jest konfigurowana w odpowiednim języku. Może to być albo w angielskiej wersji systemu Windows z odpowiedniego pakietu języka zainstalowane lub prawidłowo zlokalizowanej wersji systemu Windows.  
  
## <a name="types-of-application-that-support-bi-directional-languages"></a>Typy aplikacji tego Dwukierunkowa obsługa języków  
  
1.  Aplikacje systemu Windows. Można utworzyć aplikacji pełni dwukierunkowe, które obejmują obsługę tekstu dwukierunkowego, od prawej do lewej kolejność czytania i dublowanie (cofania układu systemu windows, menu, okna dialogowe i tak dalej). Z wyjątkiem dublowania, te funkcje są dostępne, domyślnie lub jako ustawienia właściwości. Dublowanie jest obsługiwane z założenia niektórych funkcji, takich jak pola komunikatów. Jednak w innych przypadkach należy zaimplementować dublowania w kodzie. Aby uzyskać więcej informacji, zobacz [dwukierunkowe pomocy technicznej dla aplikacji systemu Windows Forms](http://msdn.microsoft.com/Library/7b622fa4-f390-4e4d-b624-83a1917cccf2).  
  
2.  Aplikacje sieci Web. Usługi sieci Web pomocy technicznej i odbieranie wysyłania tekst UTF-8 i Unicode, udostępnia je w odpowiednich dla aplikacji obejmujących językach dwukierunkowych. Aplikacji klienta sieci Web zależne od przeglądarki dla interfejsu użytkownika, więc stopień Obsługa dwukierunkowych w aplikacji sieci Web jest zależne od tego, jak przeglądarka obsługuje te funkcje dwukierunkowe. W programie Visual Studio można utworzyć aplikacji z obsługą tekstu arabskiego lub hebrajską, kolejność czytania od prawej do lewej, kodowanie pliku i ustawienia lokalnego kultury. Aby uzyskać więcej informacji, zobacz [Dwukierunkowa obsługa aplikacji sieci Web ASP.NET](http://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).  
  
3.  Aplikacje konsoli. Aplikacje konsoli nie zawierają tekst Obsługa języków dwukierunkowych. Jest to konsekwencją jak działa z aplikacji konsoli systemu Windows.  
  
## <a name="visual-studio-features-that-are-fully-supported"></a>Funkcje programu Visual Studio, które są w pełni obsługiwane  
 W czasie projektowania w programie Visual Studio można użyć językach dwukierunkowych w następujący sposób:  
  
-   **Wpisywanie tekstu** Visual Studio obsługuje Unicode, więc jeśli system jest ustawiony na język i odpowiednich ustawień regionalnych można wprowadzić tekst w arabski lub hebrajski. (Obsługa Arabic obejmuje Kashida i znaków diakrytycznych.)  
  
-   **Nazwy obiektów** języków dwukierunkowych można użyć, aby przypisać nazwy do rozwiązania, projekty, plików, folderów i tak dalej. W kodzie można użyć językach dwukierunkowych nazw zmiennych, klasy obiektu, atrybuty, metadane i inne elementy.  
  
-   **Kodowanie pliku** można zapisywać i otwierać pliki językowe lub kodowanie Unicode. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie i otwieranie plików z kodowaniem](../ide/how-to-save-and-open-files-with-encoding.md).  
  
## <a name="features-with-limited-or-no-support"></a>Funkcje z ograniczoną liczbą lub brak obsługi  
 Inne funkcje, które są wspólne dla aplikacji języków dwukierunkowych nie są całkowicie obsługiwane w programie Visual Studio lub w niektórych przypadkach w ogóle. Należą do nich następujące elementy:  
  
-   **Kolejność czytania od prawej do lewej** domyślnie przez kontrolki wprowadzania tekstu programu Visual Studio Użyj kolejność czytania od lewej do prawej. W większości przypadków standardowe gestów systemu Windows służy do przełącznika kolejność czytania. Na przykład możesz nacisnąć przycisk Shift Ctrl + Strzałka w prawo, aby przełączyć okna właściwości do obsługi kolejność czytania od prawej do lewej dla wartości właściwości.  
  
     Jednak kolejność czytania od prawej do lewej jest nieobsługiwane wszędzie w programie Visual Studio. Wyjątki obejmują:  
  
    -   Pola wyboru, listy rozwijane i inne formanty w oknach dialogowych programu Visual Studio należy zawsze używać kolejność czytania od lewej do prawej.  
  
    -   Edytor kodu (i Edytor tekstów) nie obsługuje kolejność czytania od prawej do lewej. Można wprowadzić tekst w języku dwukierunkowa, ale kolejność odczytu jest zawsze od lewej do prawej.  
  
## <a name="naming-things-using-arabic-or-hebrew-text"></a>Nazw elementów przy użyciu arabski lub hebrajski tekstu  
 Arabski lub hebrajski tekstu służy można przypisać nazwy do folderów, zmienne i inne obiekty. Podczas pracy z arabski, można użyć znaków arabskich tym Kashida i znaków diakrytycznych.  
  
 Następujące elementy może nosić przy użyciu arabskiego lub hebrajskiego i będzie obsługiwany poprawnie w programie Visual Studio:  
  
-   Rozwiązania, projektu i nazwy pliku, w tym wszystkie foldery, które uwzględniasz w ścieżce projektu. Eksplorator rozwiązań będą wyświetlane nazwy rozwiązania, a element poprawnie.  
  
-   Zawartość pliku. Można otworzyć lub zapisywanie plików z kodowaniem Unicode lub ze stroną zaznaczony kod.  
  
    > [!NOTE]
    >  Edytor kodu jest szczególnych przypadkach. Aby uzyskać więcej informacji zobacz poniżej.  
  
-   Elementy danych. **W Eksploratorze serwera** zostanie prawidłowo wyświetlić te elementy i można je edytować.  
  
-   Elementy skopiowane do Schowka systemu Windows.  
  
-   Atrybuty i metadanych.  
  
-   Wartości właściwości. W oknie właściwości można arabski lub hebrajski tekstu. Okno służy do przełączania się między kolejność czytania od prawej do lewej i prawej do lewej strony przy użyciu standardowych klawiszy systemu Windows (CTRL + RightShift dla od prawej do lewej i CTRL + LeftShift dla od lewej do prawej).  
  
-   Kod i literały tekstowe. W edytorze kodu (która jest również edytora tekstów) umożliwia arabskiego lub hebrajską nazwy klasy, funkcje, zmiennych, właściwości, literałów ciągów, atrybuty i tak dalej. Edytor nie obsługuje jednak kolejność czytania od prawej do lewej; tekst rozpoczyna się zawsze do lewej.  
  
    > [!TIP]
    >  Zaleca się umieszczenie Literały ciągu w plikach zasobu zamiast kodować je do programu. Aby uzyskać więcej informacji, zobacz [wskazówki: Lokalizowanie formularzy systemu Windows](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
    > [!NOTE]
    >  Musi być spójna w sposób odwołań do obiektów o nazwie w tych językach. Na przykład jeśli używasz Kashida nazewnictwa Arabic zmiennej, należy zawsze używać Kashida podczas odwoływania się do tej zmiennej lub będą powodować błędy.  
  
-   Komentarze w kodzie. Komentarze można tworzyć w arabski lub hebrajski. Umożliwia także tych języków w narzędziu konstruktora komentarza.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa dwukierunkowych w systemie Windows formularzy aplikacji](http://msdn.microsoft.com/Library/7b622fa4-f390-4e4d-b624-83a1917cccf2)   
 [Dwukierunkowa obsługa aplikacji sieci Web ASP.NET](http://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03)   
 [Globalizowanie aplikacji](../ide/globalizing-applications.md)   
 [Lokalizowanie aplikacji](../ide/localizing-applications.md)