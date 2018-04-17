---
title: 'Porady: Migracja projektów rozszerzalności programu Visual Studio 2015 | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5adad311c1696d958902d9ad33ed1d1872606458
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Porady: Migracja projektów rozszerzalności programu Visual Studio 2015
Poniżej przedstawiono sposób uaktualnić Twoje rozszerzenie.  
  
> [!IMPORTANT]
>  Jeśli zamierzasz Obsługa wersji rozszerzenia rozwiązania dla starszej wersji programu Visual Studio, należy koniecznie Utwórz kopię przed przystąpieniem do uaktualniania. Może być trudne do zwrócenia uaktualnionej wersji do jego poprzedniego stanu.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Aby uaktualnić rozwiązanie rozszerzalności  
  
1.  Przy jej użyciu chcesz uaktualnić, otwórz go w nowej wersji. Książek uaktualnienie nie jest odwracalne.  
  
2.  Po zakończeniu uaktualniania, należy zmienić ścieżkę zewnętrzny program do nowej wersji devenv.exe. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**, a następnie wybierz **właściwości**. W **debugowania** karcie, znajdź pole tekstowe przez **uruchomienia programu zewnętrznego** i zmień ścieżkę devenv.exe ścieżki programu Visual Studio 2015, która powinna wyglądać mniej więcej tak:  
  
     **%ProgramFiles%\Microsoft 14.0\Common7\IDE\devenv.exe programu visual Studio**  
  
3.  Dodaj odwołanie do Microsoft.VisualStudio.Shell.14.0.dll. (Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** , a następnie wybierz **Dodaj / Reference**. Wybierz **rozszerzenia** karcie, a następnie sprawdź **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Skompiluj rozwiązanie. Tworzenie plików są wdrażane na:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< nazwa autora\>\\< Nazwa projektu\>\\< wersja projektu\>\\**.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Aby zaktualizować rozszerzalność projektu do zestawów odwołań NuGet zestawu SDK  
  
1.  Określ zestawów odwołań zestawu VS SDK potrzebne w projekcie.  W **Eksploratora rozwiązań**, rozwiń węzeł projektu **odwołania** węzła i przejrzyj listę odwołań do projektu.  Zestawy odwołań zestawu VS SDK mają prefiks **Microsoft.VisualStudio** w nazwie (na przykład: Microsoft.VisualStudio.Shell.14.0).  
  
2.  Usuwanie zestawów odwołań zestawu VS SDK z projektu, wybierając je, kliknij prawym przyciskiem myszy i **Usuń**.  
  
3.  Dodaj wersji NuGet zestawów odwołań zestawu VS SDK.  Nadal w **odwołania do Eksploratora rozwiązań** otworzyć węzła **Zarządzaj pakietami NuGet...**  okna dialogowego.  Jeśli chcesz dowiedzieć się więcej na temat tego okna dialogowego, zobacz [interfejsu użytkownika Menedżera pakietów](/NuGet/Tools/Package-Manager-UI). Zestawy odwołań zestawu SDK są publikowane w [nuget.org](http://www.nuget.org) przez [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Przy użyciu **nuget.org** jako sieci **źródła pakietu**, wyszukaj nazwę pakietu NuGet odpowiadającego zestaw żądaną odwołania (na przykład: Microsoft.VisualStudio.Shell.14.0) i zainstaluj go w sieci Projekt.  NuGet mogą dodawać wiele zestawów odwołań w celu spełnienia zależności zestawu początkowej.  
  
     Jeśli wolisz, wszystkie zestawy odwołań zestawu SDK można dodać jednocześnie przez zainstalowanie zestawu VS SDK [Meta pakietu](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Można również przełączyć przy użyciu narzędzi kompilacji zestawu VS SDK w wersji NuGet. Ten pakiet NuGet jest [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) i raz dodane do projektu zostanie obejmują niezbędne narzędzia i pliki, aby można było utworzyć projekt rozszerzalności na komputerze bez zainstalowany zestaw SDK programu VS docelowe.  
  
> [!NOTE]
>  Nie jest wymagane, aktualizowanie istniejącego rozszerzalności projektów narzędzia i zestawy odwołań NuGet.  Może nadal kompilować przy użyciu zestawów odwołań i narzędzi zainstalowanych przy użyciu zestawu VS SDK.