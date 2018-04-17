---
title: Kompilowanie i tworzenia w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/14/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ce6cf8cada1bbca4acad74b0df37ffa7d0c656a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="compiling-and-building-in-visual-studio"></a>Kompilowanie i tworzenia w programie Visual Studio

Uruchamianie kompilacji tworzy zestawy i wykonywalny aplikacji z kodu źródłowego w dowolnym momencie podczas cyklu programowania. Ogólnie rzecz biorąc proces kompilacji jest bardzo podobny przez wiele typów inny projekt, takich jak Windows, ASP.NET, aplikacje mobilne i inne. Proces kompilacji jest bardzo podobne także w językach programowania, takich jak C#, Visual Basic, C++ i F #. 

Tworzenie kodu często, można szybko zidentyfikować błędy kompilacji, takie jak niepoprawną składnię, błędnie wpisane słowa kluczowe i wpisz niezgodności. Można również szybkie wykrywanie i poprawić błędy środowiska wykonawczego, takich jak błędów logicznych i błędy semantyczne często tworzenia i uruchamiania wersje kodu do debugowania.  

To pomyślnego utworzenia kompilacji jest zasadniczo weryfikacji, że kod źródłowy aplikacji zawiera poprawną składnię i wszystkie statyczne odwołania do bibliotek, zestawy i inne składniki zostały rozwiązane. Daje to plik wykonywalny aplikacji, który można następnie pod kątem prawidłowego działania w obu [debugowania środowiska](../debugger/index.md) i za pomocą różnych testy ręczne i automatyczne do [zweryfikować jakości kodu](../test/improve-code-quality.md). Po w pełni przetestowany aplikacji można następnie kompilować wersji, aby wdrożyć na klientach. Aby obejrzeć wprowadzenie do tego procesu, zobacz [wskazówki: Kompilowanie aplikacji](../ide/walkthrough-building-an-application.md).  

W ramach rodziny produktów Visual Studio, istnieją trzy metody, można użyć do utworzenia aplikacji: środowiska IDE programu Visual Studio, narzędzia wiersza polecenia programu MSBuild i Team Foundation Build w Visual Studio Team Services:
 
| Metoda kompilacji | Zalety | 
| --- |--- | --- |  
| IDE |-Kompilacji od razu utworzyć i przetestować je w debugerze.<br />-Uruchamianie wielu procesorów kompilacji dla projektów C++ i C#.<br />-Dostosować różnych aspektów system kompilacji. |
| Wiersz polecenia programu MSBuild| -Kompilacji projektów bez instalowania programu Visual Studio.<br />-Wykonywania wielu procesorów kompilacje dla wszystkich typów projektów.<br />-Dostosować większość obszarów system kompilacji.|
| Team Foundation Build | -Automatyzacji procesu kompilacji w ramach ciągłej integracji/ciągłego dostarczania potoku.<br />-Zastosuj testów automatycznych z każdej kompilacji.<br />-Zastosowana nieograniczoną zasoby oparte na może do procesów kompilacji.<br />-Modyfikowanie przepływu pracy kompilacji i tworzenie działań kompilacji do wykonywania zadań ściśle dostosowany.|  

Dokumentacja w tej sekcji przechodzi w stan szczegółowe informacje o procesie kompilacji na podstawie IDE. Aby uzyskać więcej informacji na temat innych metod, zobacz [MSBuild](../msbuild/msbuild.md) i [ciągłej integracji i wdrażania](https://www.visualstudio.com/docs/build/overview)odpowiednio.

## <a name="overview-of-building-from-the-ide"></a>Omówienie tworzenia z IDE  

Podczas tworzenia projektu Visual Studio tworzone domyślne konfiguracje kompilacji projektu i rozwiązania, który zawiera projekt.  Te konfiguracje definiują sposób rozwiązania i projekty są wbudowane i wdrożone. Konfiguracje projektu w szczególności są unikatowe dla docelowej platformy (na przykład systemu Windows lub Linux) i zbudować typu (np. debugowanie czy wydanie). Te konfiguracje można edytować, jednak, a można też utworzyć własne konfiguracji zgodnie z potrzebami.

Pierwszy wprowadzenie do tworzenia w środowisku IDE, zobacz [wskazówki: Kompilowanie aplikacji](walkthrough-building-an-application.md).  

Następnie możesz zapoznać się [kompilowanie oraz Oczyszczanie projektów i rozwiązań w programie Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) Aby dowiedzieć się więcej o dostosowywaniu różne aspekty możesz wprowadzić do procesu. Obejmują dostosowania [zmiana katalogów wyjściowych](how-to-change-the-build-output-directory.md), [Określanie niestandardowych zdarzenia kompilacji](specifying-custom-build-events-in-visual-studio.md), [Zarządzanie zależności projektu](how-to-create-and-remove-project-dependencies.md), [Zarządzanie kompilacji dziennika pliki](how-to-view-save-and-configure-build-log-files.md), i [pomijanie ostrzeżeń kompilatora](how-to-suppress-compiler-warnings.md).

Z tego miejsca można eksplorować wielu innych zadań:
- [Zrozumienie konfiguracje kompilacji](understanding-build-configurations.md)
- [Informacje o platformach kompilacji](understanding-build-platforms.md)
- [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md).  
- Określanie zdarzeń kompilacji w [C#](how-to-specify-build-events-csharp.md) i [Visual Basic](how-to-specify-build-events-visual-basic.md). 
- [Ustawianie opcji kompilacji](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Tworzenie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## <a name="see-also"></a>Zobacz także  

- [Kompilowanie (Kompilacja) projektach witryny sieci Web](http://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)   
