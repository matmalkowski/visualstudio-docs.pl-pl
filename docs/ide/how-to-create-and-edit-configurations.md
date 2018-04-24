---
title: 'Porady: tworzenie i edycja konfiguracji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/21/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97d30f421f7c893410e563b89fd7a33fe539f141
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-and-edit-configurations"></a>Porady: tworzenie i edycja konfiguracji
Można utworzyć kilka konfiguracje kompilacji rozwiązania. Na przykład można skonfigurować kompilację debugowania, służącego do znajdowania i rozwiązywania problemów z testerów i można skonfigurować różne rodzaje kompilacje, które mogą być dystrybuowane do różnych klientów.  

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  

## <a name="create-build-configurations"></a>Tworzenie konfiguracji kompilacji  

Można użyć **programu Configuration Manager** okno dialogowe, aby wybrać lub zmodyfikuj istniejące konfiguracje kompilacji lub utworzyć nowe.  

Aby otworzyć **programu Configuration Manager** okna dialogowego, **Eksploratora rozwiązań**, otwórz menu skrótów dla rozwiązania, a następnie wybierz pozycję **programu Configuration Manager**.  

> [!NOTE]
> Jeśli **programu Configuration Manager** polecenia nie są wyświetlane w menu skrótów poszukać w polu **kompilacji** menu na pasku menu. Jeśli nie pojawia się istnieje, albo na pasku menu wybierz **narzędzia** > **opcje**, a następnie w okienku po lewej stronie z **opcje** okna dialogowego rozwiń **Projekty i rozwiązania** > **ogólne**, a w okienku po prawej stronie wybierz **Pokaż zaawansowane konfiguracje kompilacji** pole wyboru.  

W **programu Configuration Manager** okno dialogowe, można użyć **aktywnej konfiguracji rozwiązania** listy rozwijanej wybierz konfigurację rozwiązania na poziomie kompilacji, zmodyfikuj istniejącą lub Utwórz nową Konfiguracja. Można użyć **platformy aktywne rozwiązanie** listy rozwijanej do wybierz platformę wskazuje Konfiguracja zmodyfikować istniejący lub dodać nowej platformie. **Projektu kontekstów** okienko Lista projektów w rozwiązaniu. Dla każdego projektu można wybierz konfigurację specyficzną dla projektu i platformy, modyfikowania istniejących, lub Utwórz nową konfigurację lub dodać nowej platformie. Możesz również wybrać pola wyboru, które wskazują, czy każdy projekt jest dołączana w przypadku korzystania z konfiguracji całego rozwiązania do tworzenia lub wdrażania rozwiązania.  

 Po skonfigurowaniu konfiguracje, które mają można ustawić właściwości projektu, które są odpowiednie dla tych konfiguracji.  

### <a name="to-set-properties-based-on-configurations"></a>Aby ustawić właściwości konfiguracji  

-   W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz pozycję **właściwości**.  

     **Strony właściwości** zostanie otwarte okno.  

     Można ustawić właściwości dla konfiguracji. Na przykład dotyczące konfiguracji wydania, można określić czy kod jest zoptymalizowany po utworzeniu rozwiązania, a dla konfiguracji debugowania, można określić, że `DEBUG` znajduje się symbol kompilacji warunkowej. Aby uzyskać więcej informacji o ustawieniach strony właściwości, zobacz [Zarządzanie właściwościami projektów i rozwiązań](../ide/managing-project-and-solution-properties.md).  

## <a name="create-and-modify-project-configurations"></a>Tworzyć i modyfikować konfiguracje projektu  

### <a name="to-create-a-project-configuration"></a>Aby utworzyć konfigurację projektu  

1.  Otwórz **programu Configuration Manager** okno dialogowe.  

2.  Wybierz projekt w **projektu** kolumny.  

3.  W **konfiguracji** listy rozwijanej dla tego projektu, wybierz **nowy**.  

     **Nową konfigurację projektu** zostanie otwarte okno dialogowe.  

4.  W **nazwa** wprowadź nazwę dla nowej konfiguracji.  

5.  Aby użyć wartości właściwości z istniejącej konfiguracji projektu, w **Kopiuj ustawienia** listy rozwijanej wybierz konfigurację.  

6.  Aby utworzyć konfigurację całego rozwiązania w tym samym czasie, wybierz **Utwórz nową konfigurację rozwiązania** pole wyboru.  

### <a name="to-rename-a-project-configuration"></a>Aby zmienić konfigurację projektu  

1.  Otwórz **programu Configuration Manager** okno dialogowe.  

2.  W **projektu** kolumny, wybierz projekt, który ma konfigurację projektu chcesz zmienić.  

3.  W **konfiguracji** listy rozwijanej dla tego projektu, wybierz **Edytuj**.  

     **Edytuj konfiguracje projektu** zostanie otwarte okno dialogowe.  

4.  Wybierz nazwę konfiguracji projektu, który chcesz zmienić.  

5.  Wybierz **zmienić**, a następnie wprowadź nową nazwę.  

## <a name="create-and-modify-solution-wide-build-configurations"></a>Tworzyć i modyfikować konfiguracje kompilacji rozwiązania www  

### <a name="to-create-a-solution-wide-build-configuration"></a>Aby utworzyć konfigurację kompilacji całego rozwiązania  

1.  Otwórz **programu Configuration Manager** okno dialogowe.  

2.  W **aktywnej konfiguracji rozwiązania** listy rozwijanej wybierz pozycję **nowy**.  

     **Nową konfigurację rozwiązania** zostanie otwarte okno dialogowe.  

3.  W **nazwa** tekst Wprowadź nazwę dla nowej konfiguracji.  

4.  Aby użyć ustawień z istniejącej konfiguracji rozwiązania, w **Kopiuj ustawienia** listy rozwijanej wybierz konfigurację.  

5.  Jeśli chcesz utworzyć konfiguracje projektu w tym samym czasie, wybierz **Utwórz nowe konfiguracje projektu** pole wyboru.  

### <a name="to-rename-a-solution-wide-build-configuration"></a>Aby zmienić konfigurację kompilacji całego rozwiązania  

1.  Otwórz **programu Configuration Manager** okno dialogowe.  

2.  W **aktywnej konfiguracji rozwiązania** listy rozwijanej wybierz pozycję **Edytuj**.  

     **Edytuj konfiguracje rozwiązania** zostanie otwarte okno dialogowe.  

3.  Wybierz nazwę konfiguracji rozwiązania, które chcesz zmienić.  

4.  Wybierz **zmienić**, a następnie wprowadź nową nazwę.  

### <a name="to-modify-a-solution-wide-build-configuration"></a>Aby zmodyfikować konfigurację rozwiązania na poziomie kompilacji  

1.  Otwórz **programu Configuration Manager** okno dialogowe.  

2.  W **aktywnej konfiguracji rozwiązania** listy rozwijanej wybierz konfigurację chcesz.  

3.  W **projektu kontekstów** okienko dla każdego projektu, zaznacz **konfiguracji** i **platformy** i wybierz opcję **kompilacji**go i czy **Wdróż** go.

## <a name="see-also"></a>Zobacz także  
 [Zrozumienie konfiguracje kompilacji](../ide/understanding-build-configurations.md)   
 [Tworzenie i wyczyścić projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md)

