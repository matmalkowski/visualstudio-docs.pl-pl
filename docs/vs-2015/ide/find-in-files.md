---
title: Znajdź w plikach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2f6f51f53642f0eb17cbbae5498ce1c4c288a867
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676581"
---
# <a name="find-in-files"></a>Znajdź w plikach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Znajdź w plikach](https://docs.microsoft.com/visualstudio/ide/find-in-files).  
  
Znajdź w plikach ** umożliwia wyszukiwanie określonego zestawu plików. Liczba znalezionych dopasowań i akcje wykonywane są wymienione w **Find Results** wybranego w oknie **wyniku opcje**.  
  
 Można użyć dowolnej z następujących metod, do wyświetlenia **Znajdź w plikach** w **Znajdź i Zamień** okna.  
  
### <a name="to-display-find-in-files"></a>Aby wyświetlić Znajdź w plikach  
  
1.  Na pasku menu wybierz **Edytuj**, **Znajdź i Zamień**.  
  
2.  Wybierz **Znajdź w plikach**.  
  
 Aby anulować operację wyszukiwania, naciśnij klawisze CTRL + BREAK.  
  
> [!NOTE]
>  Znajdź i Zamień narzędzie nie wyszukuje katalogów przy użyciu `Hidden` lub `System` atrybut.  
  
## <a name="find-what"></a>Znajdź  
 Aby wyszukać nowy ciąg tekstowy lub wyrażenie, należy je określić w polu. Aby wyszukać dowolne z 20 ciągów, które wyszukiwane ostatnio, Otwórz listę, a następnie wybierz parametry, dla której chcesz wyszukać. Wybierz sąsiadujących **Konstruktor wyrażeń** przycisk, jeśli chcesz użyć co najmniej jednego wyrażenia regularne w wyszukiwanym ciągu. Aby uzyskać więcej informacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="look-in"></a>Szukaj w  
 Opcja wybrana z **Szukaj w** listy rozwijanej określa, czy **Znajdź w plikach** wyszukiwanie tylko w obecnie aktywnych plików lub wszystkie pliki przechowywane w określonych folderach. Z listy wybierz zakres wyszukiwania lub kliknij przycisk **przeglądania (...)**  przycisk, aby wyświetlić **Choose Search Folders** okno dialogowe i wprowadzania własnego zestawu katalogów. Możesz również wpisać ścieżkę bezpośrednio do **przeszukania** pole.  
  
> [!WARNING]
>  Za pomocą **całe rozwiązanie** lub **bieżący projekt** pliki opcje, projektów i rozwiązań nie są przeszukiwane. Jeśli chcesz zobaczyć w plikach projektu wybierz folder wyszukiwania.  
  
> [!NOTE]
>  Jeśli **przeszukania** wybrana opcja powoduje, że użytkownik może wyszukiwać pliku, który został wyewidencjonowany z kontrolą kodu źródłowego, przeszukiwany jest tylko wersja tego pliku, który został pobrany na komputer lokalny.  
  
## <a name="include-subfolders"></a>Uwzględnij podfoldery  
 Określa, że podfoldery **przeszukania** folderu zostaną przeszukane.  
  
## <a name="find-options"></a>Opcje znajdowania  
 Można rozwinąć lub zwinąć **opcje szukania** sekcji. Następujące opcje można zaznaczyć lub wyczyścić:  
  
 Uwzględnij wielkość liter  
 Po wybraniu **Find Results** wyszukiwania jest uwzględniana wielkość liter  
  
 Uwzględnij całe wyrazy  
 Po wybraniu **Find Results** windows zwróci tylko całe wyrazy dopasowań.  
  
 Używanie wyrażeń regularnych  
 Jeśli to pole wyboru jest zaznaczone, można użyć notacji specjalne do definiowania wzorców tekstu do dopasowania w **Znajdź** lub **Zamień** pól tekstowych. Aby uzyskać listę tych notacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Spójrz na następujące typy plików  
 Ta lista wskazuje typy plików, aby wyszukiwać w **przeszukania** katalogów. Jeśli to pole jest puste, wszystkie pliki w **przeszukania** katalogi będą przeszukiwane.  
  
 Wybierz dowolny element na liście, aby wprowadzić wstępnie wyszukiwany ciąg, który zawiera pliki określonego typu.  
  
## <a name="result-options"></a>Opcje wyników  
 Można rozwinąć lub zwinąć **wyniku opcje** sekcji. Następujące opcje można zaznaczyć lub wyczyścić:  
  
 Znajdź wyniki 1 okno  
 Po wybraniu wyniki bieżące wyszukiwanie spowoduje zastąpienie zawartości **Znajdź wyniki 1** okna. To okno zostanie otwarty automatycznie do wyświetlenia wyników wyszukiwania. Aby ręcznie otworzyć to okno, wybierz **Windows inne** z **widoku** menu i wybierz polecenie **Znajdź wyniki 1**.  
  
 Znajdź wyniki 2 okno  
 Po wybraniu wyniki bieżące wyszukiwanie spowoduje zastąpienie zawartości **Znajdź wyniki 2** okna. To okno zostanie otwarty automatycznie do wyświetlenia wyników wyszukiwania. Aby ręcznie otworzyć to okno, wybierz **Windows inne** z **widoku** menu i wybierz polecenie **Znajdź wyniki 2**.  
  
 Wyświetl tylko nazwy pliku  
 Wyświetla listę plików zawierających, search dopasowuje zamiast wyświetlanie wyszukiwanie pasuje do siebie.  
  
 Dołącz wyniki  
 Dołącza wyniki wyszukiwania do wcześniejszych wyników wyszukiwania.  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)   
 [Zastąp w plikach](../ide/replace-in-files.md)   
 [Visual Studio — polecenia](../ide/reference/visual-studio-commands.md)



