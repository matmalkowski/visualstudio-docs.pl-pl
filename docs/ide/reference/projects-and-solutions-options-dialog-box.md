---
title: "Projekty i rozwiązania, opcje — Okno dialogowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d7b122c66c4fd49cbc8939e5770c56fe8bc48b78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="projects-and-solutions-options-dialog-box"></a>Opcje projektów i rozwiązań — okno dialogowe
Ustawia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zachowanie związane z projektów i rozwiązań. Aby uzyskać dostęp do tych opcji, zaznacz **Narzędzia > Opcje** rozwiń **projekty i rozwiązania**i kliknij przycisk **ogólne**.

Do ustawiania domyślnych ścieżek folderów projektów i szablon **lokalizacje** kartę w tym samym oknie dialogowym.
  
> [!NOTE]
>  Opcje dostępne w oknach dialogowych i nazwy i lokalizacje poleceń menu, które zostanie wyświetlone, może się różnić od co to jest opisany w pomocy, w zależności od wersji lub aktywne ustawienia. Ta strona pomocy został zapisany z **programowanie ogólne ustawienia** pamiętać. Aby wyświetlić lub zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="general-tab-options"></a>Opcje na karcie Ogólne

**Zawsze pokazuj listy błędów Jeżeli kompilacja zakończy się z błędami**  
Otwiera **listy błędów** okna po zakończeniu kompilacji, tylko wtedy, gdy nie można utworzyć projektu. Są wyświetlane błędy występujące podczas procesu kompilacji. Po wyłączeniu tej opcji nadal występują błędy, ale nie można otworzyć okna po zakończeniu kompilacji. Ta opcja jest domyślnie włączona.  

**Śledzenie aktywnego elementu w Eksploratorze rozwiązań**  
Po wybraniu **Eksploratora rozwiązań** automatycznie zostanie otwarty i aktywny element jest zaznaczony. Zmiany wybranego elementu podczas pracy z różnych plików w projekcie lub rozwiązaniu lub różnych składników w projektancie. Jeśli ta opcja jest wyczyszczone, zaznaczenie w **Eksploratora rozwiązań** nie zmienia się automatycznie. Ta opcja jest domyślnie włączona.  

**Pokaż zaawansowane konfiguracje kompilacji**  
Po wybraniu opcji konfiguracji kompilacji są wyświetlane na **stron właściwości projektów** okno dialogowe i **strony właściwości rozwiązania** okno dialogowe. Po wyczyszczeniu opcji konfiguracji kompilacji nie występują na **stron właściwości projektów** okno dialogowe i **strony właściwości rozwiązania** okno dialogowe [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektów zawierające jedną konfigurację lub dwie konfiguracje debug i release. Jeśli projekt ma konfigurację zdefiniowane przez użytkownika, są wyświetlane opcje konfiguracji kompilacji.  

Jeśli niezaznaczone, poleceń na **kompilacji** menu, takich jak **Kompiluj rozwiązanie**, **Kompiluj ponownie rozwiązanie**, i **czystą rozwiązania**, są wykonać konfigurację wydania i poleceń na **debugowania** menu, takich jak **Rozpocznij debugowanie** i **uruchomić bez debugowania**, są wykonywane na Konfiguracja debugowania.  

**Zawsze pokazuj rozwiązania**  
Po wybraniu rozwiązanie i wszystkie polecenia, które mają wpływ na rozwiązania są zawsze wyświetlane w IDE. Po wyczyszczeniu wszystkich projektów są tworzone jako autonomiczny projekty i rozwiązania w Eksploratorze rozwiązań lub poleceń, które działają nie jest wyświetlany na rozwiązań w środowisku IDE, jeśli rozwiązanie zawiera tylko jeden projekt.  

**Zapisz nowe projekty podczas tworzenia**  
W przypadku wybrania, można określić lokalizację projektu w **nowy projekt** okno dialogowe. Po wyczyszczeniu wszystkich nowych projektów są tworzone jako tymczasowe projekty. Podczas pracy z tymczasowe projekty można tworzyć i eksperymentować projektu bez konieczności określania lokalizacji na dysku.  

**Ostrzega użytkownika, gdy lokalizacja projektu nie jest zaufany**  
Próba utworzenia nowego projektu lub otworzyć istniejącego projektu w lokalizacji, która nie jest w pełni zaufany (na przykład na ścieżkę UNC lub ścieżki HTTP), zostanie wyświetlony komunikat. Ta opcja umożliwia określenie, czy komunikat jest wyświetlany za każdym razem, który przystąpieniem do tworzenia lub otwierania projektu w lokalizacji, która nie jest w pełni zaufany.  

**Pokaż okno dane wyjściowe, gdy rozpoczyna się kompilacja**  
Automatycznie wyświetla w oknie danych wyjściowych w IDE na początku rozwiązania kompilacji. Aby uzyskać więcej informacji, zobacz [porady: kontrolowanie w oknie danych wyjściowych](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858).

**Monituj o symboliczną zmianę nazwy podczas zmiany nazwy plików**  
Po wybraniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Wyświetla pole komunikat z pytaniem, czy należy również zmienić wszystkie odwołania do projektu do elementu kodu.  

**Monituj przed przeniesieniem pliki do nowej lokalizacji**  
Po wybraniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wyświetla komunikat potwierdzenia przed lokalizacji plików są zmieniane przez akcje w Eksploratorze rozwiązań. 

## <a name="locations-tab-options"></a>Lokalizacje karta Opcje

**Lokalizacja projektów**  
Określa domyślną lokalizację gdzie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tworzy nowe projekty i rozwiązania folderów. Kilka okien dialogowych również użyć lokalizacji zestawu w tej opcji dla folderu punkty początkowe. Na przykład okno dialogowe otwarcia projektu używa tej lokalizacji skrótu Moje projekty.  

**Lokalizacja szablonów projektu użytkownika**  
Określa domyślną lokalizację który **nowy projekt** okno dialogowe używa w celu utworzenia listy **Moje szablony**. Aby uzyskać więcej informacji, zobacz [porady: Znajdź i organizowanie szablonów](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  

**Lokalizacja szablonów elementu użytkownika**  
Określa domyślną lokalizację który **Dodaj nowy element** okno dialogowe używa w celu utworzenia listy **Moje szablony**. Aby uzyskać więcej informacji, zobacz [porady: Znajdź i organizowanie szablonów](../../ide/how-to-locate-and-organize-project-and-item-templates.md). 

## <a name="see-also"></a>Zobacz też  
- [Okno dialogowe Opcje, projekty i rozwiązania, tworzenie i uruchamianie](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)  
- [Okno dialogowe Opcje, projekty i rozwiązania, projekty sieci Web](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)