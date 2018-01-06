---
title: "Konfiguracja rozwiązania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 129f86fae5de5501d72b0cdbe5e261717e60e780
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="solution-configuration"></a>Konfiguracja rozwiązania
Konfiguracje rozwiązania przechowywania właściwości poziomu rozwiązania. Bezpośrednie ich zachowanie **Start** klucza (F5) i **kompilacji** poleceń. Domyślnie te polecenia skompilować i uruchomić z konfiguracji debugowania. Zarówno polecenie zostanie wykonane w ramach konfiguracji rozwiązania. Oznacza to, że użytkownik może spodziewać się F5 do uruchamiania i kompilacji, niezależnie od aktywne rozwiązanie są konfigurowane za pomocą ustawienia. Środowisko zaprojektowano w celu optymalizacji dla rozwiązania, a nie projektów po przejściu do tworzenia i uruchamiania.  
  
 Standardowym pasku narzędzi Visual Studio zawiera przycisk Start i konfiguracji rozwiązania listy rozwijanej z prawej strony przycisk Start. Ta lista umożliwia użytkownikom wybierz konfigurację można uruchomić po naciśnięciu klawisza F5, Utwórz własne konfiguracje rozwiązania lub Edytuj istniejącą konfigurację.  
  
> [!NOTE]
>  Nie ma żadnych interfejsów rozszerzeń do tworzenia lub edytowania konfiguracje rozwiązania. Należy użyć `DTE.SolutionBuilder`. Istnieją jednak rozszerzalności interfejsów API do zarządzania kompilacji rozwiązania. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Oto, jak można zaimplementować konfiguracje rozwiązania obsługiwane przez użytkownika typu projektu:  
  
-   Projekt  
  
     Wyświetla nazwy projektów znalezione w bieżącym rozwiązaniu.  
  
-   Konfiguracja  
  
     Podaj listę konfiguracje obsługiwane przez użytkownika typu projektu i wyświetlane na stronach właściwości implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.  
  
     Kolumna konfiguracji Wyświetla nazwę konfiguracji projektu do kompilacji w tej konfiguracji rozwiązania i zawiera wszystkie konfiguracje projektu, klikając przycisk strzałki. Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> metodę, aby wypełnić tej listy. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metody wskazuje, czy projekt obsługuje edytowania konfiguracji nowych lub Edytuj wybrane opcje są również wyświetlane pod pozycją konfiguracji. Każdy z tych opcji Uruchom okien dialogowych, które wywołują metody `IVsCfgProvider2` interfejs do edycji konfiguracji projektu.  
  
     Jeśli projekt nie obsługuje konfiguracji, kolumnie konfiguracji wyświetla Brak i jest wyłączona.  
  
-   Platforma  
  
     Wyświetla platformę konfiguracji wybranego projektu kompilacji dla i wyświetla listę wszystkich dostępnych platform dla projektu, klikając przycisk strzałki. Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> metodę, aby wypełnić tej listy. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metody wskazuje, czy projekt obsługuje edytowania platform, nowe lub Edytuj wybrane opcje są również wyświetlane pod nagłówkiem platformy. Każdy z tych opcji Uruchom okien dialogowych, które wywołują `IVsCfgProvider2` metod do edycji projektu dostępnych platform.  
  
     Jeśli projekt nie obsługuje platform, w kolumnie platformy dla tego projektu Brak Wyświetla i jest wyłączona.  
  
-   Kompilacja  
  
     Określa, czy projekt jest budowany przy bieżącej konfiguracji rozwiązania. Niewybrane projekty nie są tworzone, gdy poleceń kompilacji poziomu rozwiązania są wywoływane niezależnie od wszelkich zależności projektu, które zawierają. Projekty nie są wybrane ma zostać utworzony nadal znajdują się w debugowanie, uruchamianie, pakowania i wdrażania rozwiązania.  
  
-   Deploy  
  
     Określa, czy użycie polecenia Start lub Wdróż przy użyciu wybranego rozwiązania konfiguracji kompilacji zostanie wdrożony projekt. Zaznaczenie tego pola będą dostępne, jeśli projekt obsługuje wdrażanie zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfejs w jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> obiektu.  
  
 Po dodaniu nowej konfiguracji rozwiązania, użytkownik może wybrać go w polu listy rozwijanej konfiguracji rozwiązania na standardowym pasku narzędzi do kompilacji i/lub uruchomić tej konfiguracji.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje konfiguracji zarządzania](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguracja projektu dla tworzenia](../../extensibility/internals/project-configuration-for-building.md)   
 [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)