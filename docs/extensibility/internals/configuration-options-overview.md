---
title: "Omówienie opcji konfiguracji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0edfe84e26a9331b8c40ec24b00387768bdbba82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-options-overview"></a>Omówienie opcji konfiguracji
Projekty w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] może obsługiwać wiele konfiguracji, które mogą być tworzone, debugowany, uruchamiania i/lub wdrożone. Konfiguracja jest opisane nazwany zestaw właściwości, zwykle przełączniki kompilatora i lokalizacje plików typu kompilacji. Domyślnie nowe rozwiązania zawiera dwie konfiguracje Debug i Release. Te konfiguracje mogą być stosowane przy użyciu ustawień domyślnych, lub zmodyfikować, aby spełniały określone wymagania rozwiązania lub projektu. Niektóre pakiety mogą być tworzone na dwa sposoby: edytorem ActiveX lub jako składnik w miejscu. Projekty nie trzeba jednak obsługuje wiele konfiguracji. Jeśli jest dostępny tylko jedną konfigurację, że konfiguracja jest mapowany do wszystkich konfiguracji rozwiązania.  
  
 Konfiguracje zwykle składają się z dwóch części — Nazwa konfiguracji, (na przykład Debug i Release) i ustawienia platformy. Nazwa platformy konfiguracji identyfikuje środowisko, które Ustaw cele konfiguracji, takich jak interfejs API lub Platforma systemu operacyjnego. Użytkownicy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie można utworzyć platformy; musi wybrać z wybór projektu umożliwia pakiet VSPackage. Podczas instalacji użytkownika pakiet VSPackage, platforma dostarczania utworzone podczas tworzenia pakietu można powierzchni dowolną nazwę platformy żądanego na podstawie kryteriów ustawiony przez autora pakietu. Użytkownik może następnie wybrać na liście platform udostępniane przez pakiet VSPackage są uruchomione na stronach właściwości.  
  
 Nazwy platformy są opcjonalne, ponieważ nie wszystkie projekty obsługuje pojęcie platform. W konfiguracji nie ma nazwę platformy, ciąg "Brak" jest wyświetlana w Interfejsie użytkownika.  
  
 Każde rozwiązanie ma swój własny zestaw konfiguracji, tylko jeden z nich mogą być aktywne w czasie. Konfiguracja rozwiązania to zestaw nie więcej niż jedną konfigurację z każdego projektu. Jest ustalenie "nie więcej niż" z powodu opcję, aby wykluczyć projektu z konfiguracji rozwiązania. Użytkownicy mogą tworzyć własne konfiguracje niestandardowe rozwiązania.  
  
 W poniższej tabeli przedstawiono typowe konfiguracje instalacji dla projektu. Wiersze są oznaczane etykietami z nazwami konfiguracji i kolumny z nazwami platformy.  
  
|Nazwa konfiguracji|Platform — Win32|Platform — Win64|  
|------------------------|----------------------|----------------------|  
|Debugowanie|\<Ustawienia Win32 debugowania >|\<Ustawienia Win64 debugowania >|  
|Wydanie|\<Zwolnij Win32 Ustawienia >|\<Zwolnij Win64 Ustawienia >|  
|MyConfig|Brak|\<Ustawienia MyConfig Win64 >|  
  
> [!NOTE]
>  Nie można utworzyć konfiguracji rozwiązania "MyConfig", który nie obejmuje platformy "Win32", chyba że docelowych projektu nie obsługuje systemu Win32.  
  
 Zmiana aktywnej konfiguracji rozwiązania wybiera zbiór konfiguracje projektu, które są wbudowane, uruchamianie, debugowania lub wdrożone w tym rozwiązaniu. Na przykład jeśli zmienisz aktywnej konfiguracji rozwiązania z wersji do debugowania wszystkie projekty w tym rozwiązaniu automatycznie są tworzone za projektów konfiguracji określonej w konfiguracji debugowania tego rozwiązania. Konfiguracje projekty są zwykle również debugowania o nazwie, chyba że użytkownik wprowadził ręczne wprowadzanie zmian w środowisku programu Configuration Manager.  
  
 Właściwości konfiguracji rozwiązania, które są przechowywane dla każdego projektu obejmują nazwę projektu, nazwa konfiguracji projektu, flagi, aby wskazać, czy do tworzenia lub wdrażania i nazwę platformy. Aby uzyskać więcej informacji, zobacz [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md).  
  
 Użytkownik może wyświetlać i ustaw parametry konfiguracji rozwiązania wybierając rozwiązania w hierarchii (Eksploratorze rozwiązań) i otwieranie stron właściwości. Podobnie możesz wyświetlić i ustawić parametry konfiguracji projektu wybierając projekt w Eksploratorze rozwiązań i otwieranie stron właściwości dla tego projektu.  
  
 Użytkownika można również tworzyć jednego projektu przy użyciu ustawienia konfiguracji wydania i wszystkie pozostałe z ustawienia konfiguracji debugowania, jeśli to konieczne. Aby uzyskać więcej informacji, zobacz [konfiguracji projektu dla tworzenia](../../extensibility/internals/project-configuration-for-building.md).  
  
 Na poniższym diagramie przedstawiono, jak są zaimplementowane interfejsy, które obsługują konfiguracje rozwiązania i projektu:  
  
 ![Grafika interfejsy konfiguracji](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfejsy konfiguracji  
  
 Kilka uwag odnoszących się do poprzedniego diagramu:  
  
-   `IDispatch`jest oznaczona jako opcjonalna w obiekcie konfiguracji. W szczególności jest opcjonalny do interfejsy Konfiguracja w obiekcie przeglądania.  
  
-   `IVsDebuggableProjectCfg`oznaczone jako opcjonalne w obiekt konfiguracji, ale jest wymagany do obsługi debugowania.  
  
-   `IVsProjectCfg2`oznaczone jako opcjonalne w obiekt konfiguracji, ale jest wymagany dla danych wyjściowych grupowanie pomocy technicznej.  
  
-   `Config Provider` Obiekt jest oznaczony jako opcjonalny obiekt, ale ta opcja jest gdzie go zaimplementować. Obiekt może wdrożyć na obiekt project lub oddzielny obiekt.  
  
-   `IVsCfgProvider2`jest potrzebne do obsługi platform i edytowania konfiguracji. `IVsCfgProvider`wystarczy, jeśli nie należy implementować te funkcje.  
  
-   Niektóre z tych obiektów przedstawione na diagramie oddzielnych obiektów mogą być połączone w tej samej klasy, w przypadku, gdy praktyczne zgodnie z wymaganiami określonego projektu. W innych tematach w tej sekcji jednak te obiekty i interfejsy skojarzone z tymi obiektami, zostanie dokładnie omówione zgodnie ze scenariuszem przedstawione na diagramie.  
  
-   Niektóre obiekty zostały zaimplementowane oddzielnie. Na przykład projektu i tworzenia rozwiązania są dokonywane na oddzielnych wątkach i obiekt do zarządzania życie kompilacji oddzielnie od obiektu opisujące konfiguracji dla kompilacji.  
  
 Więcej informacji o interfejsach obiekt konfiguracji i obiekt dostawcy konfiguracji w poprzedni diagram, zobacz [obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md). Ponadto [konfiguracji projektu dla tworzenia](../../extensibility/internals/project-configuration-for-building.md) zamieszczono więcej informacji dotyczących interfejsy konstruktora konfiguracji i obiekt zależności kompilacji i [konfiguracji projektu wdrożenia zarządzania](../../extensibility/internals/project-configuration-for-managing-deployment.md) dokładniej opisuje interfejsy dołączony do narzędzia wdrażania konfiguracji i wdrażania zależności obiektów. Na koniec [konfiguracji projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md) opisano grupy danych wyjściowych i dane wyjściowe obiektu interfejsów i używanie stron właściwości do wyświetlania i ustawiania właściwości zależne od konfiguracji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Konfiguracja projektu dla tworzenia](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)