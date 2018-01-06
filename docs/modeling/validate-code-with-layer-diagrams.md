---
title: "Weryfikacja kodu przy użyciu diagramów zależności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: "82"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: 1e9041c397b121a5919ad370ccb7020c229e9b61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="validate-code-with-dependency-diagrams"></a>Weryfikacja kodu przy użyciu diagramów zależności

**Najnowsze informacje**: zobacz [ten wpis w blogu](https://blogs.msdn.microsoft.com/visualstudioalm/2016/11/30/live-dependency-validation-in-visual-studio-2017/).

[Wideo: Sprawdzanie poprawności zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 

## <a name="why-use-dependency-diagrams"></a>Dlaczego warto używać diagramy zależności?

Aby upewnić się, że kod nie koliduje to z jego projekt, sprawdź poprawność kodu przy użyciu diagramów zależności w programie Visual Studio. Może to ułatwić:  
  
-   Znajdź konfliktów między zależności w kodzie i zależności na diagramie zależności.  
  
-   Znajdowanie zależności, na które mogły mieć wpływ proponowane zmiany.  
  
     Na przykład można edytować na diagramie zależności, aby wyświetlić potencjalnych architektura zmiany, a następnie zweryfikować kod w celu wyświetlenia odpowiednich zależności.  
  
-   Refaktoryzację lub migrację kodu do innego projektu.  
  
     Znajdowanie kodu lub zależności, które wymagają pracy przy przenoszeniu kodu do innej architektury.  
  
 **Wymagania**  
  
-   Visual Studio  
  
-   Visual Studio na serwerze Team Foundation Build, aby sprawdzić poprawność kodu automatycznie z Team Foundation Build  
  
-   Rozwiązania, które ma diagramu zależności projektu modelowania. Na tym wykresie zależności muszą być połączone z artefaktami w projektach Visual C# .NET i Visual Basic .NET, które chcesz zweryfikować. Zobacz [tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Aby dowiedzieć się, które wersje programu Visual Studio obsługują tę funkcję, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Można sprawdzić poprawność kodu ręcznie z diagramu otwartych zależności w programie Visual Studio lub z wiersza polecenia. Kod możesz również walidować automatycznie podczas uruchamiania lokalnych kompilacji lub programu Team Foundation Build. Zobacz [Channel 9 wideo: projektowania i walidacji architektury przy użyciu diagramów zależności](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
> [!IMPORTANT]
>  Jeśli chcesz uruchamiać weryfikacji warstwy z Team Foundation Build, należy również zainstalować tę samą wersję programu Visual Studio na serwerze kompilacji.  
  
-   [Jeśli element obsługuje weryfikacji](#SupportsValidation)  
  
-   [Zawierają inne zestawy .NET i projekty do sprawdzania poprawności](#IncludeReferences)  
  
-   [Ręcznie Sprawdź poprawność kodu](#ValidateManually)  
  
-   [Weryfikacja kodu automatycznie](#ValidateAuto)  
  
-   [Rozwiązać problemy z weryfikacją warstwy](#TroubleshootingValidation)  
  
-   [Zrozumienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors)  

## <a name="live-dependency-validation"></a>Sprawdzanie poprawności zależności na żywo

W tej wersji programu Visual Studio walidacji zależności występuje w czasie rzeczywistym, a błędy są wyświetlane od razu w oknie Lista błędów w usłudze Visual Studio.

* Sprawdzanie poprawności na żywo jest obsługiwana dla C# i Visual języku. 

* Aby włączyć pełną analizę rozwiązania, za pomocą walidacji zależności na żywo, Otwórz ustawienia opcji pasku złota, który pojawi się na liście błędów. 
 - Można zignorować ten pasek gold trwale, jeśli nie jest konieczne wyświetlenie wszystkich problemów architektury w rozwiązaniu.
 - Jeśli nie włączysz Pełna analiza rozwiązania analizy odbywa się tylko w przypadku plików edytowany.<p /> 

* Uaktualnianie projektów można włączyć weryfikację na żywo, okno dialogowe będzie wyświetlany postęp konwersji.

* Podczas aktualizowania projektu do walidacji zależności na żywo, wersja pakietu NuGet jest uaktualniany do być takie same dla wszystkich projektów i jest najwyższa wersja w użyciu. 

* Dodawanie nowych wyzwalaczy projektu walidacji zależności Aktualizacja projektu. 
  
##  <a name="SupportsValidation"></a>Jeśli element obsługuje weryfikacji  
 Możesz połączyć warstwy do witryn sieci Web, dokumentów pakietu Office, pliki w formacie zwykłego tekstu i pliki w projektach, które są współużytkowane przez wielu aplikacji, ale proces weryfikacji nie obejmują ich. Błędy walidacji nie będą widoczne w przypadku odwołań do projektów lub zestawów połączonych z oddzielnymi warstwami, jeżeli między tymi warstwami nie ma żadnych zależności. Odwołania te nie są uważane za zależności, chyba że w kodzie wykorzystano te odwołania.  
  
1.  Na diagramie zależności, wybierz jeden lub kilku warstw, kliknij prawym przyciskiem myszy zaznaczenie, a następnie kliknij **Wyświetl łącza**.  
  
2.  W **Explorer warstwy**, obejrzyj **weryfikacji obsługuje** kolumny. Jeśli wartością jest false, element nie obsługuje walidacji.  
  
##  <a name="IncludeReferences"></a>Zawierają inne zestawy .NET i projekty do sprawdzania poprawności  
 Przeciągnij elementy do diagramu zależności, odwołania do odpowiednich zestawów platformy .NET lub projekty są dodawane automatycznie **odwołuje się do warstwy** folderu projektu modelowania. Folder ten zawiera odwołania do zestawów i projektów, które są analizowane podczas walidacji. Bez ręcznie przeciągając je do diagramu zależności może zawierać innych zestawów platformy .NET i projekty do weryfikacji.  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt modelowania lub **odwołania warstwy** folder, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, wybierz zestawy lub projektów, a następnie kliknij przycisk **OK**.  
  
##  <a name="ValidateManually"></a>Ręcznie Sprawdź poprawność kodu  
 Jeśli masz diagramu otwartych zależności, który jest połączony z elementów rozwiązania, możesz uruchomić **weryfikacji** polecenia skrót z diagramu. Umożliwia także wiersza polecenia do uruchomienia **msbuild** z **/p:ValidateArchitecture** ustawioną właściwość niestandardowa **True**. Na przykład, po wprowadzeniu dowolnych zmian w kodzie należy regularnie wykonywać walidację warstwy tak, aby można było wcześnie wychwycić konflikty zależności.  
  
#### <a name="to-validate-code-from-an-open-dependency-diagram"></a>Weryfikacja kodu z diagramu otwartych zależności   
  
1.  Kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij przycisk **walidację architektury**.  
  
    > [!NOTE]
    >  Domyślnie **Akcja kompilacji** ma ustawioną właściwość na plik diagramu (.layerdiagram) zależności **weryfikacji** tak, aby diagramu znajduje się w trakcie tego procesu.  
  
     **Listy błędów** okna raportów o błędach. Aby uzyskać więcej informacji o błędach weryfikacji, zobacz [omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors).  
  
2.  Aby wyświetlić źródło każdy błąd, kliknij dwukrotnie ten błąd w **listy błędów** okna.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]mogą być wyświetlane mapy kodu zamiast źródła błędu. Dzieje się tak, jeśli kod ma zależność na zestaw, który nie jest określony przez wykres zależności, albo kod brakuje zależności, który jest określony przez wykres zależności. Przejrzyj mapy kodu lub kod, aby określić, czy zależność powinna istnieć. Aby uzyskać więcej informacji na temat mapy kodu, zobacz [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).  
  
3.  Aby zarządzać błędy, zobacz [Zarządzanie błędy sprawdzania poprawności](#ManageErrors).  
  
#### <a name="to-validate-code-at-the-command-prompt"></a>Aby walidować kod z wiersza polecenia  
  
1.  Otwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia.  
  
2.  Wybierz jedną z następujących opcji:  
  
    -   Aby sprawdzić poprawność kodu dla projektu modelowania określonych w rozwiązaniu, uruchom [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] z następujących właściwości niestandardowej.  
  
        ```  
        msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true  
        ```  
  
         - lub -  
  
         Przejdź do folderu, który zawiera modelowania pliku (.modelproj) i na diagramie zależności projektu, a następnie uruchom [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] z następujących właściwości niestandardowych:  
  
        ```  
        msbuild /p:ValidateArchitecture=true   
        ```  
  
    -   Aby sprawdzić poprawność kod wszystkich projektów modelowania w rozwiązaniu, uruchom [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] z następujących właściwości niestandardowych:  
  
        ```  
        msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true   
        ```  
  
         - lub -  
  
         Przejdź do folderu rozwiązania, które musi zawierać projekt modelowania, który zawiera diagram zależności, a następnie uruchom [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] z następujących właściwości niestandardowych:  
  
        ```  
        msbuild /p:ValidateArchitecture=true  
        ```  
  
     Zostaną wyświetlone wszystkie błędy. Aby uzyskać więcej informacji na temat [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], zobacz [MSBuild](../msbuild/msbuild.md) i [zadanie programu MSBuild](../msbuild/msbuild-task.md).  
  
 Aby uzyskać więcej informacji o błędach weryfikacji, zobacz [omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors).  
  
###  <a name="ManageErrors"></a>Zarządzanie błędy sprawdzania poprawności  
 Podczas procesu projektowania możesz pominąć niektóre konflikty zgłoszone podczas walidacji. Na przykład możesz pominąć błędy, które są już poprawiane lub które nie są istotne w konkretnym scenariuszu. Pomiń błąd, jest dobrą praktyką jest zalogować elementu roboczego [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].  
  
> [!WARNING]
>  Komputer musi już być połączony do TFS źródła kod sterowania (SCC) można utworzyć lub połączyć do elementu roboczego. Jeśli spróbujesz nawiązać połączenie z inną SCC TFS programu Visual Studio bieżące rozwiązanie zostanie automatycznie zamknięte. Upewnij się, czy masz już połączenie do odpowiednich SCC przed próbą utworzenia lub łącze do elementu roboczego. W nowszych wersjach programu Visual Studio poleceń menu nie są dostępne, jeśli nie są połączone SCC.  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>Aby utworzyć element roboczy dla błędu walidacji  
  
-   W **listy błędów** okna, kliknij prawym przyciskiem myszy błąd, wskaż pozycję **Utwórz element roboczy**, a następnie kliknij typ elementu roboczego, który chcesz utworzyć.  
  
 Umożliwia zarządzanie błędy sprawdzania poprawności w tych zadań **listy błędów** okno:  
  
|**Aby**|**Wykonaj następujące kroki**|  
|------------|----------------------------|  
|Pomijanie wybranych błędów podczas walidacji|Kliknij prawym przyciskiem myszy co najmniej jeden wybrany błąd, wskaż pozycję **Zarządzanie błędy sprawdzania poprawności**, a następnie kliknij przycisk **Pomiń błędy**.<br /><br /> Pominięte błędy są wyświetlane jako przekreślone. Przy następnym uruchomieniu walidacji te błędy nie pojawią się.<br /><br /> Błędy pomijane są śledzone w pliku .suppressions odpowiedni plik diagramu zależności.|  
|Zaprzestanie pomijania wybranych błędów|Kliknij prawym przyciskiem myszy wybrany błąd pominięty lub błędy, wskaż pozycję **Zarządzanie błędy sprawdzania poprawności**, a następnie kliknij przycisk **błędów Stop pomijanie**.<br /><br /> Wybrane pominięte błędy pojawią się przy następnym uruchomieniu walidacji.|  
|Przywróć wszystkie pominięty błędów w **listy błędów** okna|Kliknij prawym przyciskiem myszy **listy błędów** okna, wskaż **Zarządzanie błędy sprawdzania poprawności**, a następnie kliknij przycisk **Pokaż wszystkie pominięte błędy**.|  
|Ukryj błędy wszystkich pominięty z **listy błędów** okna|Kliknij prawym przyciskiem myszy **listy błędów** okna, wskaż **Zarządzanie błędy sprawdzania poprawności**, a następnie kliknij przycisk **Ukryj wszystkie błędy pomijane**.|  
  
##  <a name="ValidateAuto"></a>Weryfikacja kodu automatycznie  
 Walidację warstwy możesz wykonać przy każdym uruchomieniu lokalnej kompilacji. Jeśli Twój zespół używa programu Team Foundation Build, możesz wykonać walidację warstwy z bramkowanymi ewidencjonowaniami, którą można określić, tworząc niestandardowe zadanie MSBuild, a następnie używając raportów kompilacji do zbierania błędów walidacji. Aby utworzyć warunkowe zaewidencjonowanie kompilacji, zobacz [aby zatwierdzić zmiany, użyj procesu kompilacji warunkowe zaewidencjonowanie](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>Aby walidować kod automatycznie podczas lokalnej kompilacji  
  
-   Użyj edytora tekstów, aby otworzyć plik projektu modelowania (.modelproj), a następnie dołącz następującą właściwość:  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \-lub -  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt modelowania, który zawiera zależności diagramu lub diagramy, a następnie kliknij przycisk **właściwości**.  
  
2.  W **właściwości** Ustaw projekt modelowania **walidację architektury** właściwości **True**.  
  
     Dotyczy to projektów modelowania w trakcie procesu walidacji.  
  
3.  W **Eksploratora rozwiązań**, kliknij plik diagramu (.layerdiagram) zależności, który ma być używany do sprawdzania poprawności.  
  
4.  W **właściwości** okna, upewnij się, że diagram **Akcja kompilacji** właściwość jest ustawiona na **weryfikacji**.  
  
     Dotyczy to również na diagramie zależności w trakcie tego procesu.  
  
 Aby zarządzać błędy w oknie Lista błędów, zobacz [Zarządzanie błędy sprawdzania poprawności](#ManageErrors).  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Aby walidować kod automatycznie podczas działania programu Team Foundation Build  
  
1.  W **Team Explorer**, kliknij dwukrotnie definicję kompilacji, a następnie kliknij przycisk **procesu**.  
  
2.  W obszarze **parametrów procesu kompilacji**, rozwiń węzeł **kompilacji**i wpisz następujące polecenie w **argumenty programu MSBuild** parametru:  
  
     `/p:ValidateArchitecture=true`  
  
 Aby uzyskać więcej informacji o błędach weryfikacji, zobacz [omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors). Aby uzyskać więcej informacji na temat [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)], zobacz:  
  
-   [Tworzenie aplikacji](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
-   [Użyj domyślnej szablonu procesu kompilacji](http://msdn.microsoft.com/Library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
-   [Modyfikowanie kompilacji starszych opartego na UpgradeTemplate.xaml](http://msdn.microsoft.com/Library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
-   [Dostosuj szablon procesu kompilacji](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
-   [Monitoruj postęp kompilacji uruchomiona](http://msdn.microsoft.com/Library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
##  <a name="TroubleshootingValidation"></a>Rozwiązać problemy z weryfikacją warstwy  
 W poniższej tabeli opisano problemy związane z walidacją warstwy i ich rozwiązania. Problemy te różnią się od błędów, które wynikają z konfliktów między kodem i projektem. Aby uzyskać więcej informacji o tych błędach, zobacz [omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors).  
  
|**Problem**|**Możliwa przyczyna**|**Rozdzielczość**|  
|---------------|------------------------|--------------------|  
|Błędy walidacji nie występują w oczekiwany sposób.|Sprawdzanie poprawności nie działa na diagramach zależności, które są kopiowane z innych diagramów zależności w Eksploratorze rozwiązań i które znajdują się w tym samym projekcie modelowania. Diagramy zależności, które są kopiowane w ten sposób zawierają tego samego odwołania, co oryginalna diagram zależności.|Dodaj nowy diagram zależności do projektu modelowania.<br /><br /> Skopiować elementy z diagramu zależności źródła do nowego diagramu.|  
  
##  <a name="UnderstandingValidationErrors"></a>Opis i rozwiązywanie błędów walidacji warstwy  
 Podczas sprawdzania poprawności kod diagram zależności błędy sprawdzania poprawności wystąpić, gdy kod jest w konflikcie z projektu. Na przykład następujące warunki mogą powodować występowanie błędów walidacji:  
  
-   Artefakt jest przypisany do niewłaściwej warstwy. W takim przypadku przenieś artefakt.  
  
-   Artefakt, taki jak klasa, używa innej klasy w sposób, który powoduje konflikt z architekturą. W tym przypadku zrefaktoryzuj kod, aby usunąć zależność.  
  
 Aby rozwiązać te błędy, aktualizuj kod, dopóki nie przestaną pojawiać się błędy podczas walidacji. Zadanie to możesz wykonać w sposób iteracyjny.  
  
 W poniższej sekcji opisano składnię, która jest używana w tych błędach, wyjaśniono znaczenie tych błędów i zasugerowano, co można zrobić, aby je rozwiązać lub zarządzać nimi.  
  
|**Składnia**|**Opis**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* jest artefaktu, który jest skojarzony z warstwą na diagramie zależności.<br /><br /> *ArtifactTypeN* jest typem *ArtifactN*, takich jak **klasy** lub **metody**, na przykład:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metoda)|  
|*NamespaceNameN*|Nazwa przestrzeni nazw.|  
|*LayerNameN*|Nazwa warstwy na diagramie zależności.|  
|*DependencyType*|Typ relacji zależności między *Artifact1* i *Artifact2*. Na przykład *Artifact1* ma **wywołania** relacji z *Artifact2*.|  
  
|**Błąd składni**|**Opis błędu**|  
|----------------------|---------------------------|  
|DV0001: **Nieprawidłowa zależność**|Ten problem został zgłoszony, gdy element kodu (przestrzeń nazw, typu, elementu członkowskiego) zamapowany na odwołania warstwy element kodu zamapowana do innej warstwy, ale nie ma strzałki zależności między tych warstw na diagramie walidacji zależności zawierający tej warstwy. Stanowi to naruszenie ograniczenia zależności.|  
|DV1001: **nieprawidłową nazwę przestrzeni nazw**|Ten problem został zgłoszony w elemencie kodu skojarzonego z warstwy, która właściwość "Dozwolone nazw Namespace" nie zawiera przestrzeń nazw, w którym jest zdefiniowany element tego kodu. Stanowi to naruszenie ograniczenia nazewnictwa. Należy pamiętać, że ma być średnikami lista przestrzeni nazw, w którym kod elementy skojarzone z są warstwy składni "Dozwolone nazw Namespace" mogą być zdefiniowany.|  
|DV1002: **zależność od unreferenceable przestrzeni nazw**|Ten problem został zgłoszony w elemencie kodu skojarzone z warstwy i odwołuje się do innego elementu kodu zdefiniowany w przestrzeni nazw, który jest zdefiniowany we właściwości "Unreferenceable Namespace" warstwy. Stanowi to naruszenie ograniczenia nazewnictwa. Należy pamiętać, że właściwość "Unreferenceable przestrzeni nazw" jest zdefiniowana jako Rozdzielana średnikami lista przestrzenie nazw, które nie powinny być przywoływany w skojarzone z tą warstwą elementy kodu.|  
|DV1003: **niedozwolone przestrzeni nazw**|Ten problem został zgłoszony w elemencie kodu skojarzone z warstwą zawierającą właściwość "Niedozwolone nazw Namespace" w przestrzeni nazw, w którym jest zdefiniowany element tego kodu. Stanowi to naruszenie ograniczenia nazewnictwa. Należy pamiętać, że właściwość "Niedozwolone nazwę przestrzeni nazw" jest zdefiniowana jako Rozdzielana średnikami lista przestrzeni nazw, w którym kod elementy skojarzone z tą warstwą nie powinna być zdefiniowana.|  
|DV3001: **Missing Link**|Warstwa "*LayerName*"łączy się"*artefaktu*" którego nie można znaleźć. Czy nie brakuje odwołania do zestawu?|*LayerName* linki do artefaktów, którego nie można odnaleźć. Na przykład, może brakować łącza do klasy, ponieważ w projekcie modelowania brakuje odwołania do zestawu, który zawiera klasę.|  
|DV9001: **analizy architektury znaleziono błędy wewnętrzne**|Wyniki mogą być niepełne. Aby uzyskać więcej informacji, zobacz szczegółowy dziennik zdarzeń kompilacji lub okno danych wyjściowych.|Zobacz dziennik zdarzeń kompilacji lub okno danych wyjściowych, aby uzyskać więcej szczegółów.|  

 
## <a name="see-also"></a>Zobacz też  
 [Weryfikacja systemu w czasie projektowania](../modeling/validate-your-system-during-development.md)   
 [Wideo: Sprawdzanie poprawności zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   
