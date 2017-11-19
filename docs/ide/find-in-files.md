---
title: "Znajdź w plikach | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: be7da7a50003b302bf6ce8b211ff7f67d70b3e5f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="find-in-files"></a>Znajdź w plikach
**Znajdź w plikach** umożliwia wyszukiwanie określonego zestawu plików. Znalezionych dopasowań oraz działania podjęte są wymienione w **znaleźć wyników** wybrany w oknie **powoduje opcje**.  
  
 Można użyć dowolnej z następujących metod można wyświetlić **Znajdź w plikach** w **Znajdź i Zamień** okna.  
  
### <a name="to-display-find-in-files"></a>Aby wyświetlić Znajdź w plikach  
  
1.  Na pasku menu wybierz **Edytuj**, **Znajdź i Zamień**.  
  
2.  Wybierz **Znajdź w plikach**.  
  
 Aby anulować operację wyszukiwania, naciśnij klawisze CTRL + BREAK.  
  
> [!NOTE]
>  Narzędzia Znajdź i Zamień nie Szukaj katalogi z `Hidden` lub `System` atrybut.  
  
## <a name="find-what"></a>Znajdź  
 Aby wyszukać nowe ciąg tekstowy lub wyrażenie, należy określić w polu. Aby wyszukiwać dowolne ciągi 20, które można przeszukiwać ostatnio, Otwórz listę, a następnie wybierz pozycję ciągu, dla której ma nastąpić wyszukiwanie. Wybierz sąsiadujących **Konstruktor wyrażeń** przycisku, jeśli chcesz używać jednego lub wielu wyrażeń regularnych w wyszukiwanym ciągu. Aby uzyskać więcej informacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="look-in"></a>Szukaj w  
 Opcja wybrana z **Szukaj w** listy rozwijanej określa, czy **Znajdź w plikach** wyszukiwanie tylko w plikach obecnie aktywne lub wszystkie pliki przechowywane w określonych folderach. Wybierz zakres wyszukiwania z listy lub kliknij przycisk **Przeglądaj (...)**  przycisk, aby wyświetlić **wybierz foldery wyszukiwania** okno dialogowe i wprowadzania zestawu katalogów. Możesz również wpisać ścieżkę bezpośrednio do **Szukaj w** pole.  
  
> [!WARNING]
>  Z **całego rozwiązania** lub **bieżącego projektu** pliki opcje, projektu i rozwiązania nie są przeszukiwane. Jeśli chcesz wyglądały w plikach projektu, wybierz folder wyszukiwania.  
  
> [!NOTE]
>  Jeśli **Szukaj w** opcji powoduje, że użytkownik może wyszukiwać w pliku, który został wyewidencjonowany z kontroli kodu źródłowego, przeszukiwane będą tylko wersję tego pliku, do którego została pobrana na komputer lokalny.  
  
## <a name="include-subfolders"></a>Uwzględnij podfoldery  
 Określa, że podfoldery **Szukaj w** folderu zostaną przeszukane.  
  
## <a name="find-options"></a>Dostępne opcje  
 Można rozwinąć lub zwinąć **dostępne opcje** sekcji. Można zaznaczyć lub wyczyścić następujące opcje:  
  
 Uwzględnij wielkość liter  
 Po wybraniu **znaleźć wyników** wyszukiwanie będzie uwzględniana wielkość liter  
  
 Uwzględnij całe wyrazy  
 Po wybraniu **znaleźć wyników** windows zwróci tylko całe wyrazy dopasowań.  
  
 Używanie wyrażeń regularnych  
 Jeśli to pole wyboru jest zaznaczone, można użyć notacji specjalne wzorce tekstu do dopasowania w **Znajdź** lub **Zamień** pól tekstowych. Aby uzyskać listę tych notacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Obejrzyj następujące typy plików  
 Ta lista wskazuje typy plików do przeszukiwania w **Szukaj w** katalogów. Jeśli to pole jest puste, wszystkie pliki w **Szukaj w** katalogi będą wyszukiwane.  
  
 Wybierz dowolną pozycję na liście, wprowadź ciąg wyszukiwania wstępnie skonfigurowane, które zostaną znalezione pliki określonego typu.  
  
## <a name="result-options"></a>Opcje wyników  
 Można rozwinąć lub zwinąć **powoduje opcje** sekcji. Można zaznaczyć lub wyczyścić następujące opcje:  
  
 Znajdź okno wyników 1  
 Po wybraniu wyniki wyszukiwania bieżącego zastąpi zawartość **znaleźć 1 wyniki** okna. To okno zostanie otwarty automatycznie do wyświetlania wyników wyszukiwania. Aby otworzyć to okno ręcznie, zaznacz **inne okna** z **widoku** menu i wybierz polecenie **znaleźć 1 wyniki**.  
  
 Znajdź okno wyników 2  
 Po wybraniu wyniki wyszukiwania bieżącego zastąpi zawartość **znaleźć 2 wyniki** okna. To okno zostanie otwarty automatycznie do wyświetlania wyników wyszukiwania. Aby otworzyć to okno ręcznie, zaznacz **inne okna** z **widoku** menu i wybierz polecenie **znaleźć 2 wyniki**.  
  
 Wyświetl tylko nazwy plików  
 Wyświetla listę plików zawierających wyszukiwania odpowiada zamiast wyświetlanie wyszukiwania dopasowuje się.  
  
 Dołączanie wyników  
 Dołącza wyniki wyszukiwania do wyników poprzedniego wyszukiwania.  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)   
 [Zastąp w plikach](../ide/replace-in-files.md)   
 [Visual Studio — polecenia](../ide/reference/visual-studio-commands.md)