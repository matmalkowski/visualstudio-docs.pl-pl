---
title: "Tworzenie pakietów rozwiązania SharePoint | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
ms.assetid: 6b1f1fbf-fa9c-453d-80af-36ec9829677a
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe7822382443e6c1e9bc1a77eb0cd64844504172
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-sharepoint-solution-packages"></a>Tworzenie pakietów rozwiązania SharePoint
  Przy użyciu projektanta pakietów, można tworzyć i dostosowywać pakiety wdrożeniowe. Na przykład można dodać SharePoint — elementy projektu i funkcje, zresetuj na serwerze usług IIS, ustaw zakresy aktywacji funkcji i zidentyfikować zależności funkcji. Projektant również generuje manifest pliku XML, który opisuje każdego pakietu.  
  
## <a name="packaging-tools"></a>Narzędzia do tworzenia pakietów  
 Można użyć **projektanta pakietów** do dostosowywania pakietu oraz do generowania manifestu. Możesz dołączyć SharePoint — elementy projektu, skonfigurować serwer sieci Web należy zresetować i skonfigurować typ wdrożenia serwera. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 Alternatywnie można użyć **Eksploratora pakietów** Aby zmodyfikować funkcje i elementy w pliku pakietu (wsp). Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 Visual Studio i MSBuild służy do tworzenia plików pakietu (wsp) do wdrożenia rozwiązania programu SharePoint. Ten proces generuje manifestu pliki potrzebne do wdrożenia programu SharePoint. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie pakietu programu SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b) i [porady: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Opcje projektanta pakietów  
 W poniższej tabeli przedstawiono właściwości można dostosować w pakietach programu SharePoint z **projektanta pakietów**.  
  
|Pakiet właściwości projektanta|Opis ustawienia domyślne|  
|-------------------------------|------------------------------------|  
|Nazwa|Wymagany. Ma ustawioną domyślną nazwę pakietu *ProjectName*.|  
|Resetuj serwer sieci Web|Opcjonalny. Wybierz, aby ponownie uruchomić serwer sieci Web po plik wsp jest zainstalowany na serwerze programu SharePoint.|  
|Typ serwera wdrażania|Wymagany. Domyślnie zakres wynosi ApplicationServer.<br /><br /> ApplicationServer: Opis serwera, który jest hostem usług.<br /><br /> WebFrontEnd: Opis serwera, który jest hostem witryny sieci Web.|  
|Elementy w rozwiązaniu|Wszystkie SharePoint — elementy projektu i funkcje, które mogą zostać dodane do pakietu.|  
|Elementy w pakiecie|Opcjonalny. Wszystkie elementy programu SharePoint i funkcje, które mają zostać wdrożone w pakiecie.|  
  
## <a name="configuring-the-packaging-process"></a>Konfigurowanie proces tworzenia pakietu  
 Po opracowywanie rozwiązań SharePoint w Visual Studio, można dostosować sposób pakiecie projektów.  
  
 W poniższej tabeli przedstawiono dwa obiekty docelowe MSBuild, które można dostosować sposób tworzenia pliku wsp.  
  
|docelowy|Opis|  
|------------|-----------------|  
|BeforeLayout|Obiekt docelowy wykonuje zadania bezpośrednio przed pliki są kopiowane do katalogu pośrednim. Pliki można zmodyfikować przed utworzeniem pliku pakietu (wsp).|  
|AfterLayout|Obiekt docelowy, który wykonuje zadania natychmiast po pliki są kopiowane do katalogu pośrednim.|  
  
 Aby uzyskać więcej informacji [porady: Dostosowywanie pakietu rozwiązania SharePoint przy użyciu docelowych elementów MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Architektura tworzenia pakietów  
 Zostaną wykonane następujące kroki tworzenia pakietu programu SharePoint (wsp) w programie Visual Studio.  
  
1.  Funkcje i pakiety są weryfikowane, aby upewnić się, że struktury fizyczne i semantyczne pakietu jest prawidłowa.  
  
2.  Wyliczane są funkcje, elementy projektu i plików pakietu w pakiecie. Pliki manifestu pakietów i funkcje są przekształcane uwzględnienie wszystkich informacji niezbędnych do wdrożenia i aktywacji. Tokeny są zastępowane FQDN wartości.  
  
3.  Można dostosować docelowy programu BeforeLayout MSBuild jest wykonywana. Możesz utworzyć ten krok, aby wprowadzić zmiany niestandardowy pakiet przed utworzeniem pliku wsp.  
  
4.  Wyliczany pliki są kopiowane do katalogu pośrednim.  
  
5.  Można dostosować docelowy programu AfterLayout MSBuild jest wykonywana. Możesz utworzyć ten krok, aby wprowadzić zmiany niestandardowy pakiet przed utworzeniem pliku wsp.  
  
6.  Pliki w katalogu pośrednim są dodawane do pliku wsp.  
  
## <a name="package-folder-structure"></a>Struktura folderów pakietu  
 Podczas pakowania projektu SharePoint plik wsp jest utworzona w programie SolutionFolder\bin\\*BuildConfiguration* folderu. Na przykład, jeśli rozwiązanie znajduje się w *dysku*: \Visual 2013\Projects\ListDefinition1 w Studio i konfiguracji kompilacji ma ustawioną wartość wersji, plik wsp znajduje się w *dysku*: \Visual Studio 2013\ Projects\ListDefinition1\bin\Release.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Porady: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Porady: Tworzenie pakietu programu SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [Porady: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint przy użyciu docelowych elementów MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
  