---
title: "Wdrażanie zasad ewidencjonowania analizy kodu niestandardowego dla kodu zarządzanego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3d8747ddb78c257ae0ba38d24fb2c5cc529f67b9
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>Wdrażanie niestandardowych zasad ewidencjonowania analizy kodu dla kodu zarządzanego
Analiza kodu zasad ewidencjonowania określa zestaw reguł, które członkowie zespołu projektu muszą być uruchamiane na kod źródłowy, zanim zostanie on zaewidencjonowany do systemu kontroli wersji. Firma Microsoft udostępnia zestaw standard *zestawów reguł* reguł analizy kodu tej grupy do obszarów funkcjonalnych. *Zestawy reguł niestandardowych zasad ewidencjonowania* określ zestaw reguł analizy kodu, które są specyficzne dla projektu zespołowego. Zestaw reguł są przechowywane w pliku .ruleset.  
  
 Zasady ewidencjonowania są ustawione na poziomie projektu zespołowego i określony przez lokalizację plik .ruleset w drzewie kontroli wersji. Nie ma żadnych ograniczeń na lokalizację kontroli wersji team zasad niestandardowego zestawu reguł.  
  
 Analiza kodu jest skonfigurowany dla projektów poszczególnych kod w oknie właściwości dla każdego projektu. Niestandardowego zestawu reguł dla projektu kodu jest określany przez fizyczną lokalizację pliku .ruleset na komputerze lokalnym. W przypadku plik .ruleset, który znajduje się na tym samym dysku projekt kodu programu Visual Studio korzysta ze ścieżki względnej do pliku w konfiguracji projektu.  
  
 Sugerowane rozwiązanie do tworzenia zespołu projektu niestandardowego zestawu reguł jest przechowywany plik .ruleset zasad ewidencjonowania w specjalnym folderze, który nie jest częścią żadnego projektu kodu. Jeśli plik jest przechowywany w folderze dedykowanych, można zastosować uprawnienia, które ograniczają edytujący pliku reguł i mogą łatwo przenosić struktura katalogów zawierający projekt do innego katalogu lub komputera.  
  
## <a name="creating-the-team-project-custom-check-in-rule-set"></a>Tworzenia zestawu niestandardową regułę wyboru projektu zespołowego  
 Aby utworzyć niestandardowego zestawu reguł dla projektu zespołowego, należy najpierw utworzyć folderu specjalnego dla zasad ewidencjonowania zestawu reguł w **Eksploratora kontroli źródła**. Następnie utwórz pliku zestawu reguł i dodaj go do kontroli wersji. Na koniec należy określić regułę, Ustaw jako zasady analizy kodu ewidencjonowania projektu zespołowego.  
  
> [!NOTE]
>  Aby utworzyć folder w projekcie zespołowym, najpierw należy zamapować głównego projektu zespołowego do lokalizacji na komputerze lokalnym.  
  
#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Aby utworzyć folder kontroli wersji dla zestawu reguł zasad ewidencjonowania  
  
1.  W [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], rozwiń węzeł projektu zespołowego, a następnie kliknij przycisk **kontroli źródła**.  
  
2.  W **folderów** okienku kliknij prawym przyciskiem myszy projektu zespołowego, a następnie kliknij przycisk **nowy Folder**.  
  
3.  W okienku głównym kontroli źródła, kliknij prawym przyciskiem myszy **nowy Folder**, kliknij przycisk **Zmień nazwę**, a następnie wpisz nazwę dla folderu zestawu reguł.  
  
#### <a name="to-create-the-check-in-policy-rule-set"></a>Aby utworzyć zestaw reguł zasad ewidencjonowania  
  
1.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **pliku**.  
  
2.  W **kategorii** kliknij **ogólne**.  
  
3.  W **szablony** listy, kliknij dwukrotnie **zestawu reguł analizy kodu**.  
  
4.  Określ reguły do uwzględnienia w zestawie reguł, a następnie zapisz pliku zestawu reguł do utworzonego folderu zestawu reguł.  
  
     Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### <a name="to-add-the-rule-set-file-to-version-control"></a>Aby dodać regułę, ustaw pliku kontroli wersji  
  
1.  W **Eksploratora kontroli źródła**, kliknij prawym przyciskiem myszy nowy folder, a następnie kliknij przycisk **Dodaj elementy do folderu**.  
  
     Aby uzyskać więcej informacji, zobacz [Git i VSTS](/vsts/git/overview).  
  
2.  Kliknij utworzony plik zestawu reguł, a następnie kliknij przycisk **Zakończ**.  
  
     Plik zostanie dodany do kontroli źródła i wyewidencjonowane dla Ciebie.  
  
3.  W **Eksploratora kontroli źródła** okno Szczegóły, kliknij prawym przyciskiem myszy nazwę pliku, a następnie kliknij przycisk **Zaewidencjonuj oczekujące zmiany**.  
  
4.  W **zaewidencjonowania** okno dialogowe, użytkownik może dodać komentarz, a następnie kliknij przycisk **Zaewidencjonuj**.  
  
    > [!NOTE]
    >  Jeśli został już skonfigurowany dla projektu zespołowego zasad analizy kodu ewidencjonowania, jeśli wybrano **wymusić zaewidencjonowanie obejmowało tylko pliki, które są częścią bieżącego rozwiązania**, wyzwoli ostrzeżenia dotyczącego zasad awarii. W oknie dialogowym błędu zasad, wybierz **Przesłoń błąd zasad i Kontynuuj ewidencjonowanie**. Dodaj komentarz wymagane, a następnie kliknij przycisk **OK**.  
  
#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Aby określić regułę pliku zestawu jako zasady ewidencjonowania  
  
1.  Na **zespołu** menu wskaż **ustawienia projektu zespołowego**, a następnie kliknij przycisk **kontroli źródła**.  
  
2.  Kliknij przycisk **zasad ewidencjonowania**, a następnie kliknij przycisk **Dodaj**.  
  
3.  W **zasad ewidencjonowania** listy, kliknij dwukrotnie **analizy kodu**i upewnij się, że **wymusić analizy kodu dla zarządzanego kodu** pole wyboru jest zaznaczone.  
  
4.  W **Uruchom ten zestaw reguł** kliknij  **\<wybierz zestaw reguł z kontroli źródła >**.  
  
5.  Wpisz ścieżkę pliku zestawu reguł zasad ewidencjonowania w kontroli wersji.  
  
     Ścieżka musi być zgodna z następującej składni:  
  
     **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    > [!NOTE]
    >  Możesz skopiować ścieżkę przy użyciu jednej z poniższych procedur w programie **Eksploratora kontroli źródła**:  
  
    -   W **folderów** okienku, kliknij folder, który zawiera pliku zestawu reguł. Skopiuj ścieżki kontroli wersji, folderu, który jest wyświetlany w **źródła** polu, a następnie ręcznie wpisać nazwę pliku zestawu reguł.  
  
    -   W okienku szczegółów kliknij prawym przyciskiem myszy pliku zestawu reguł, a następnie kliknij przycisk **właściwości**. Na **ogólne** karcie, skopiuj wartość **nazwy serwera**.  
  
## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>Synchronizowanie projektów kodu dla zestawu reguł zasad ewidencjonowania  
 Należy określić zestaw reguł zasad ewidencjonowania projektu zespołowego jako zestaw reguł analizy kodu w konfiguracji projektu kodu, w oknie dialogowym właściwości projektu kodu. Jeśli zestaw reguł znajduje się na tym samym dysku projektu kodu, ścieżką względną służy do określania zestawu reguł, w przypadku wybrania ścieżki z okna dialogowego pliku. Umożliwia ścieżki względnej ustawienia właściwości projektu jako przenośne do innych komputerów, które używają podobne lokalnej wersji kontrolowanie struktury.  
  
#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Aby określić regułę projektu zespołowego należy ustawić jako zestawu reguł projektu kodu  
  
1.  W razie potrzeby pobrać folder zestaw reguł zasad ewidencjonowania i plik z kontroli wersji.  
  
     Można wykonać ten krok w **Eksploratora kontroli źródła** przez kliknięcie prawym przyciskiem myszy folder, a następnie klikając pozycję zestawu reguł **Pobierz najnowszą wersję**.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt kodu, a następnie kliknij przycisk **właściwości**.  
  
3.  **Kliknij przycisk analizy kodu**.  
  
4.  W razie potrzeby kliknij odpowiednie opcje w **konfiguracji** i **platformy** listy.  
  
5.  Aby uruchomić kod — analiza zawsze projekt kodu jest utworzony przy użyciu określonej konfiguracji, wybierz **Włącz analizę kodu podczas kompilacji (definiuje stała CODE_ANALYSIS)** pole wyboru.  
  
6.  Aby zignorować kodu składników innych firm, wybierz **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.  
  
7.  W **Uruchom ten zestaw reguł** kliknij  **\<Przeglądaj >**.  
  
8.  Określ lokalna wersja pliku zestawu reguł zasad ewidencjonowania.