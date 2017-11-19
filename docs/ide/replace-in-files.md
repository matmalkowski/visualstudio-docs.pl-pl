---
title: "Visual Studio Znajdź i Zamień w plikach | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8b13903fc02a716de951847ce9409e750764b123
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
# <a name="replace-in-files"></a>Zastąp w plikach
**Zastąp w plikach** umożliwia wyszukiwanie kodu określonego zestawu plików dla ciągu lub wyrażenia i zmienić niektórych lub wszystkich znalezionych dopasowań. Znalezionych dopasowań oraz działania podjęte są wymienione w **znaleźć wyników** wybrany w oknie **powoduje opcje**.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, na przykład aby **ogólne** lub **Visual C++** ustawienia, wybierz **narzędzia**, **Import i eksport ustawień**, a następnie Wybierz **zresetować wszystkie ustawienia**.
  
Można użyć dowolnej z następujących metod można wyświetlić **Zastąp w plikach** w **Znajdź i Zamień** okna.  
  
### <a name="to-display-replace-in-files"></a>Aby wyświetlić Zamień w plikach  
  
1.  Na **Edytuj** menu, rozwiń węzeł **Znajdź i Zamień**.  
  
2.  Wybierz **Zastąp w plikach**.  
  
     — lub —  
  
     Jeśli **Znajdź i Zamień** okno jest już otwarty, na pasku narzędzi, wybierz **Zastąp w plikach**.  
  
## <a name="find-what"></a>Znajdź  
Aby wyszukać nowe ciąg tekstowy lub wyrażenie, należy określić w polu. Aby wyszukiwać dowolne ciągi 20, które można przeszukiwać ostatnio, Otwórz listę, a następnie wybierz pozycję ciągu, dla której ma nastąpić wyszukiwanie. Wybierz sąsiadujących **Konstruktor wyrażeń** przycisku, jeśli chcesz używać jednego lub wielu wyrażeń regularnych w wyszukiwanym ciągu. Aby uzyskać więcej informacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).
  
## <a name="replace-with"></a>Zamień  
Aby zastąpić wystąpienia ciągu w **Znajdź** pole z innego ciągu, wpisz ciąg zastępczy w **Zamień** pole. Aby usunąć wystąpienia ciągu w **Znajdź** pozostaw to pole puste. Otwórz listę, aby wyświetlić 20 ciągów, dla których Przeszukano ostatnio. Wybierz sąsiadujących **Konstruktor wyrażeń** przycisku, jeśli chcesz używać jednego lub wielu wyrażeń regularnych w ciągu zastąpienia. Aby uzyskać więcej informacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).
  
## <a name="look-in"></a>Szukaj w  
Opcja wybrana z **Szukaj w** listy rozwijanej określa, czy **Zastąp w plikach** wyszukuje tylko w plikach obecnie aktywne lub przeszukuje wszystkie pliki przechowywane w określonych folderach. Wybierz zakres wyszukiwania z listy, wpisz ścieżkę folderu lub kliknij przycisk **Przeglądaj (...)**  przycisk, aby wyświetlić **wybierz foldery wyszukiwania** okno dialogowe i wybrać zestaw folderów do wyszukiwania. Możesz również wpisać ścieżkę bezpośrednio do **Szukaj w** pole.
  
> [!NOTE]
>  Jeśli **Szukaj w** opcji powoduje, że użytkownik może wyszukiwać w pliku, który został wyewidencjonowany z kontroli kodu źródłowego, przeszukiwane będą tylko wersję tego pliku, do którego została pobrana na komputer lokalny.
  
## <a name="find-options"></a>Dostępne opcje  
Można rozwinąć lub zwinąć **dostępne opcje** sekcji. Można zaznaczyć lub wyczyścić następujące opcje:  
  
Uwzględnij wielkość liter  
Po wybraniu **znaleźć wyników** windows będą wyświetlane tylko wystąpienia **Znajdź** ciąg, który jest zgodny zarówno przez zawartość, jak i w przypadku. Na przykład, wyszukaj "MyObject" z **wielkość liter** wybrane będzie zwracać "MyObject", ale nie "myobject" lub "MYOBJECT."  

Uwzględnij całe wyrazy  
Po wybraniu **znaleźć wyników** windows będą wyświetlane tylko wystąpienia **Znajdź** parametry, które są dopasowywane w kompletne wyrazy. Na przykład wyszukaj "MyObject" zwróci "MyObject", ale nie "CMyObject" lub "MyObjectC."  

Używanie wyrażeń regularnych  
Gdy to pole wyboru jest zaznaczone, można użyć notacji specjalne wzorce tekstu w **Znajdź** lub **Zamień** pól tekstowych. Aby uzyskać listę tych notacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  

Obejrzyj następujące typy plików  
Ta lista wskazuje typy plików do przeszukiwania w **Szukaj w** katalogów. Jeśli to pole pozostanie puste, wszystkie pliki w **Szukaj w** katalogi będą wyszukiwane.  

Wybierz dowolną pozycję na liście, wprowadź ciąg wyszukiwania wstępnie skonfigurowane, które zostaną znalezione pliki określonego typu.  
  
## <a name="result-options"></a>Opcje wyników  
Można rozwinąć lub zwinąć **powoduje opcje** sekcji. Można zaznaczyć lub wyczyścić następujące opcje:  

Znajdź okno wyników 1  
Po wybraniu wyniki wyszukiwania bieżącego zastąpi zawartość **znaleźć 1 wyniki** okna. To okno zostanie otwarty automatycznie do wyświetlania wyników wyszukiwania. Aby otworzyć to okno ręcznie, zaznacz **inne okna** z **widoku** menu i wybierz polecenie **znaleźć 1 wyniki**.  

Znajdź okno wyników 2  
Po wybraniu wyniki wyszukiwania bieżącego zastąpi zawartość **znaleźć 2 wyniki** okna. To okno zostanie otwarty automatycznie do wyświetlania wyników wyszukiwania. Aby otworzyć to okno ręcznie, zaznacz **inne okna** z **widoku** menu i wybierz polecenie **znaleźć 2 wyniki**.  

Wyświetl tylko nazwy plików  
Gdy to pole wyboru jest zaznaczone, windows wyniki Znajdź listę pełnej nazwy i ścieżki dla wszystkich plików, które zawierają ciąg wyszukiwania. Jednak wyniki nie będą zawierać wiersz kodu, w którym pojawi się ciąg. To pole wyboru jest dostępne dla Znajdź w plikach tylko.  

Kontynuuj modyfikowanie otwartych plików po Zamień wszystkie  
Po wybraniu pozostawia otwarte wszystkie pliki, w których zostały wprowadzone wymiany, więc można cofnąć lub zapisać zmiany. Ograniczenia pamięci może ograniczyć liczbę plików, które mogą pozostawać otwarte po operacji Zastąp.  

> [!CAUTION]
>  Można użyć **Cofnij** tylko na plikach, które pozostają otwarte do edycji. Jeśli ta opcja nie jest wybrana, pliki, które nie zostały już otworzyć do edycji pozostanie zamknięty, a nie **Cofnij** opcji będzie dostępna w tych plikach.  
  
## <a name="see-also"></a>Zobacz także
[Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)   
[Znajdź w plikach](../ide/find-in-files.md)   
[Visual Studio — polecenia](../ide/reference/visual-studio-commands.md)