---
title: Tworzenie pakietów rozwiązania SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 957789c4adfc476429179ed84f87f544c0d37143
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765274"
---
# <a name="create-sharepoint-solution-packages"></a>Tworzenie pakietów rozwiązania SharePoint
  Przy użyciu projektanta pakietów, można tworzyć i dostosowywać pakiety wdrożeniowe. Na przykład można dodać SharePoint — elementy projektu i funkcje, zresetuj na serwerze usług IIS, ustaw zakresy aktywacji funkcji i zidentyfikować zależności funkcji. Projektant również generuje manifest pliku XML, który opisuje każdego pakietu.  
  
## <a name="packaging-tools"></a>Narzędzia do tworzenia pakietów
 Można użyć **projektanta pakietów** do dostosowywania pakietu oraz do generowania manifestu. Możesz dołączyć SharePoint — elementy projektu, skonfigurować serwer sieci Web należy zresetować i skonfigurować typ wdrożenia serwera. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 Alternatywnie można użyć **Eksploratora pakietów** Aby zmodyfikować funkcje i elementy w pliku pakietu (*.wsp*). Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 Można użyć do utworzenia pakietu Visual Studio i MSBuild (*WSP*) pliki do wdrożenia rozwiązania programu SharePoint. Ten proces generuje manifestu pliki potrzebne do wdrożenia programu SharePoint. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie pakietu programu SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b) i [porady: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Opcje projektanta pakietów
 W poniższej tabeli przedstawiono właściwości można dostosować w pakietach programu SharePoint z **projektanta pakietów**.  
  
|Pakiet właściwości projektanta|Opis ustawienia domyślne|  
|-------------------------------|------------------------------------|  
|Nazwa|Wymagana. Ma ustawioną domyślną nazwę pakietu *ProjectName*.|  
|Resetuj serwer sieci Web|Opcjonalna. Wybierz, jeśli chcesz ponownie uruchomić serwer sieci Web po *WSP* plik jest zainstalowany na serwerze programu SharePoint.|  
|Typ serwera wdrażania|Wymagana. Domyślnie zakres wynosi ApplicationServer.<br /><br /> ApplicationServer: Opis serwera, który jest hostem usług.<br /><br /> WebFrontEnd: Opis serwera, który jest hostem witryny sieci Web.|  
|Elementy w rozwiązaniu|Wszystkie SharePoint — elementy projektu i funkcje, które mogą zostać dodane do pakietu.|  
|Elementy w pakiecie|Opcjonalna. Wszystkie elementy programu SharePoint i funkcje, które mają zostać wdrożone w pakiecie.|  
  
## <a name="configure-the-packaging-process"></a>Skonfiguruj proces tworzenia pakietu
 Po opracowywanie rozwiązań SharePoint w Visual Studio, można dostosować sposób pakiecie projektów.  
  
 W poniższej tabeli przedstawiono dwa obiekty docelowe MSBuild, które można dostosować sposób *WSP* tworzony jest plik.  
  
|docelowy|Opis|  
|------------|-----------------|  
|BeforeLayout|Obiekt docelowy wykonuje zadania bezpośrednio przed pliki są kopiowane do katalogu pośrednim. Pliki można zmodyfikować przed utworzeniem pliku pakietu (*.wsp*).|  
|AfterLayout|Obiekt docelowy, który wykonuje zadania natychmiast po pliki są kopiowane do katalogu pośrednim.|  
  
 Aby uzyskać więcej informacji [porady: Dostosowywanie pakietu rozwiązania SharePoint przy użyciu docelowych elementów MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Architektura tworzenia pakietów
 Zostaną wykonane następujące kroki w przypadku utworzenia pakietu programu SharePoint (*WSP*) w programie Visual Studio.  
  
1.  Funkcje i pakiety są weryfikowane, aby upewnić się, że struktury fizyczne i semantyczne pakietu jest prawidłowa.  
  
2.  Wyliczane są funkcje, elementy projektu i plików pakietu w pakiecie. Pliki manifestu pakietów i funkcje są przekształcane uwzględnienie wszystkich informacji niezbędnych do wdrożenia i aktywacji. Tokeny są zastępowane FQDN wartości.  
  
3.  Można dostosować docelowy programu BeforeLayout MSBuild jest wykonywana. Możesz utworzyć ten krok, aby wszelkie modyfikacje niestandardowy pakiet przed *WSP* tworzony jest plik.  
  
4.  Wyliczany pliki są kopiowane do katalogu pośrednim.  
  
5.  Można dostosować docelowy programu AfterLayout MSBuild jest wykonywana. Możesz utworzyć ten krok, aby wszelkie modyfikacje niestandardowy pakiet przed *WSP* tworzony jest plik.  
  
6.  Pliki w katalogu pośrednim zostaną dodane do *WSP* pliku.  
  
## <a name="package-folder-structure"></a>Struktura folderów pakietu
 Podczas pakowania projektu programu SharePoint, *.wsp* pliku jest tworzony w *SolutionFolder\bin\{BuildConfiguration}* folderu. Na przykład, jeśli rozwiązanie jest w *2013\Projects\ListDefinition1 C:\Visual Studio* i konfiguracji kompilacji ma ustawioną wartość wersji *.wsp* plik znajduje się w *2013\ C:\Visual Studio Projects\ListDefinition1\bin\Release*.  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Porady: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Porady: Tworzenie pakietu programu SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [Porady: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint przy użyciu docelowych elementów MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
 