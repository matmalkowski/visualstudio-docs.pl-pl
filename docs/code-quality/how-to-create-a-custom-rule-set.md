---
title: "Porady: Tworzenie niestandardowego zestawu reguł | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.addremoverulesets
helpviewer_keywords: Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e9cba33565af81a76d043a3fc3f63eef831e1ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-custom-rule-set"></a>Porady: tworzenie niestandardowego zestawu reguł
W [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)], i [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], można tworzyć i modyfikować niestandardowy *zestaw reguł* do określonego projektu potrzeb skojarzonych z analizy kodu. Aby utworzyć regułę niestandardową wartość, otwórz je lub zestawów reguł więcej standardowe w edytorze zestawu reguł. Można dodać lub usunąć określone zasady i akcji, który występuje podczas analizy kodu Określa, że naruszono reguły można zmienić.  
  
 Aby utworzyć nową regułę niestandardową zestaw, zapisz go przy użyciu nowej nazwy pliku. Zestaw reguł niestandardowych zostanie automatycznie przypisany do projektu.  
  
## <a name="opening-the-rule-set-editor"></a>Otwieranie reguły edytorze zestawu  
  
#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Aby otworzyć pustą pliku zestawu reguł w edytorze zestawu reguł  
  
1.  Na **pliku** menu [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], wskaż polecenie **nowy** , a następnie kliknij przycisk **pliku**.  
  
2.  W **nowy plik** okno dialogowe, kliknij przycisk **ogólne** w **zainstalowane szablony** listy, a następnie wybierz **zestawu reguł analizy kodu**.  
  
3.  Zostanie wyświetlony Edytor zestawu reguł. Na liście edytor nie zaznaczono żadnych reguł.  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Aby utworzyć niestandardową regułę z jednej istniejącego zestawu reguł  
  
1.  W Eksploratorze rozwiązań kliknij projekt prawym przyciskiem myszy, a następnie wybierz **właściwości**.  
  
2.  Na **właściwości** , kliknij pozycję **analizy kodu**.  
  
3.  W **zestawu reguł** listy rozwijanej, wykonaj jedną z następujących czynności:  
  
    -   Wybierz zestaw reguł, który chcesz dostosować.  
  
     \-lub -  
  
    -   Wybierz  **\<Przeglądaj >** określ zestaw istniejącej reguły, których nie ma na liście.  
  
4.  Kliknij przycisk **Otwórz** reguły są wyświetlane w edytorze zestawu reguł.  
  
#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Aby utworzyć regułę niestandardową zestaw z wielu istniejących zestawów reguł  
  
1.  W Eksploratorze rozwiązań kliknij projekt prawym przyciskiem myszy, a następnie wybierz **właściwości**.  
  
2.  Na **właściwości** , kliknij pozycję **analizy kodu**.  
  
3.  Wybierz  **\<Wybierz zestawy wielu reguł... >** z **Uruchom ten zestaw reguł**.  
  
4.  W **Dodawanie lub usuwanie zestawów reguł** wybierz pozycję zestawów reguł, na którym chcesz utworzyć nowego zestawu reguł, a następnie kliknij przycisk **OK**.  
  
5.  Zapisz nowy zestaw reguł.  
  
     Nazwa nowego zestawu reguł jest zaznaczona w **Uruchom ten zestaw reguł** listy. Można zmienić nazwę wyświetlaną dla zestawu reguł w następnym kroku.  
  
6.  (Opcjonalnie) Aby zmienić nazwę wyświetlaną w zestawie reguł na **widoku** menu, kliknij przycisk **okna właściwości**. Wpisz nazwę wyświetlaną w **nazwa** pole.  
  
7.  Aby dodać, usunąć, lub zmodyfikować reguł analizy kodu określonych w nowym zestawie reguł, kliknij przycisk **Otwórz**.  
  
## <a name="modifying-a-rule-set"></a>Modyfikowanie zestawu reguł  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Aby zmodyfikować reguły ustawić w edytorze zestawu reguł  
  
-   Aby zmienić nazwę wyświetlaną w zestawie reguł na **widoku** menu, kliknij przycisk **okna właściwości**. Wprowadź nazwę wyświetlaną w **nazwa** pole. Należy zauważyć, że nazwa wyświetlana może się różnić od nazwy pliku.  
  
-   Aby dodać zasady grupy do niestandardowego zestawu reguł, zaznacz pole wyboru grupy. Aby usunąć zasady grupy, wyczyść pole wyboru.  
  
-   Aby dodać regułę określonego zestawu reguł niestandardowych, zaznacz pole wyboru reguły. Aby usunąć regułę w zestawie reguł, usuń zaznaczenie pola wyboru.  
  
-   Aby zmienić Akcja podejmowana, gdy naruszenia reguły analizy kodu, kliknij w **akcji** reguły do pola, a następnie wybierz jedną z następujących wartości:  
  
     **Ostrzegaj** -generuje ostrzeżenie.  
  
     **Błąd** -generuje błąd.  
  
     **Brak** — wyłącza regułę. Ta akcja jest taka sama jak usunięcie reguły z zestawu reguł.  
  
## <a name="changing-the-rule-set-editor-display"></a>Zmiana reguły ustawić wyświetlania edytora  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Do grupy, filtrowanie, lub zmień pola w edytorze zestawu reguł za pomocą paska narzędzi edytora zestawu reguł  
  
-   Aby rozszerzyć reguł we wszystkich grupach, kliknij przycisk **Rozwiń wszystkie**.  
  
-   Aby zwinąć reguł we wszystkich grupach, kliknij przycisk **Zwiń wszystkie**.  
  
-   Aby zmienić pole reguły są grupowane według, wybierz pola z **Group By** listy. Aby wyświetlić zasady rozgrupować, zaznacz  **\<Brak >**.  
  
-   Aby dodać lub usunąć pola w kolumnach regułę, kliknij przycisk **opcje kolumny**.  
  
-   Aby ukryć reguł, które nie mają zastosowanie do bieżącego rozwiązania **Ukryj reguł, które nie mają zastosowanie do bieżącego rozwiązania**.  
  
-   Aby przełączyć między pokazywanie i ukrywanie reguł, które są przypisane Akcja błędu, kliknij przycisk **Pokaż reguły, które mogą generować błędy analizy kodu**.  
  
-   Aby przełączyć między pokazywanie i ukrywanie reguł, które są przypisane ostrzeżenie akcję, kliknij przycisk **Pokaż reguły, które mogą generować ostrzeżenia analizy kodu**.  
  
-   Aby przełączyć między pokazywanie i ukrywanie reguł, które są przypisane **Brak** działania, kliknij przycisk **Pokaż reguły, które nie są włączone**.  
  
-   Aby dodać lub usunąć domyślną regułę ustawia bieżący zestaw reguł firmy Microsoft, kliknij przycisk **Dodaj lub usuń podrzędne zestawy reguł**.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Konfigurowanie analizy kodu dla projektu zarządzanego kodu](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Odwołanie zestawu reguł analizy kodu](../code-quality/code-analysis-rule-set-reference.md)