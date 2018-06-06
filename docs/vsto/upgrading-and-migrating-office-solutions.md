---
title: Uaktualnienie i migracja rozwiązań pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 364eaf87bc8760320acc1edfe74adebd1adcc0bd
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767276"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Uaktualnienie i migracja rozwiązań pakietu Office
  Jeśli masz program Microsoft Office project, który został utworzony we wcześniejszej wersji programu Visual Studio, należy uaktualnić projekt, aby użyć go w bieżącej wersji programu Visual Studio. Aby uaktualnić program Microsoft Office project, otwórz go w wersji programu Visual Studio, który zawiera narzędzia Microsoft Office developer tools. Aby uzyskać więcej informacji o wersjach programu Visual Studio, które obejmują narzędzia Microsoft Office developer tools, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
> [!NOTE]  
>  Program Visual Studio nie może uaktualnić InfoPath formularza szablonu projektów, które zostały utworzone przy użyciu poprzedniej wersji programu Visual Studio. Tych typów projektów nie są obsługiwane w bieżącej wersji programu Visual Studio.  
  
## <a name="changes-to-upgraded-projects"></a>Zmiany w uaktualnionych projektów  
 Po uaktualnieniu programu Microsoft Office project Visual Studio modyfikuje projekt pod kątem następujących elementów:  
  
-   Visual Studio 2010 Tools dla pakietu Office runtime. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for Office runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Bieżący odwołania do zestawu.  
  
-   Wersja programu .NET Framework, która jest obsługiwana przez ten typ projektu (po uaktualnieniu do programu Visual Studio 2013 tylko).  
  
-   Wersja pakietu Microsoft Office, który jest obsługiwany przez ten typ projektu (po uaktualnieniu do programu Visual Studio 2013 tylko).  
  
## <a name="assembly-references"></a>Odwołania do zestawów  
 Visual Studio uaktualnia następujące odwołania do zestawów w projekcie:  
  
-   Microsoft Office podstawowe zestawy międzyoperacyjne (PIAs).  
  
-   Zestawy w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Aby uzyskać więcej informacji o tych zestawów, zobacz [Visual Studio Tools for Office runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Nowe lub zaktualizowane wersje zestawów zależnych.  
  
## <a name="targeted-net-framework"></a>Docelowej platformy .NET Framework  
 Po uaktualnieniu projektu do programu Visual Studio 2013, Visual Studio modyfikuje projekt docelowy: [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] lub [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Wersja programu .NET framework celem projektu zależy od tego, jaka wersja pakietu Office została zainstalowana na tym komputerze. Jeśli [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] jest zainstalowany, program Visual Studio modyfikuje projektu do docelowego [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. W przeciwnym razie program Visual Studio modyfikuje projektu do docelowego [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
> [!NOTE]  
>  Czasami trzeba wykonać kilka dodatkowych kroków, aby uruchomić rozwiązanie retargeted na komputerach użytkowników końcowych i rozwoju i projektu nie będą możliwe, gdy jest używana niektórych funkcji. Aby uzyskać więcej informacji, zobacz [rozwiązań Office migracji do programu .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 W przypadku skierowania [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później w projektach pakietu Office, można używać niektórych funkcji, które nie są dostępne, jeśli zostanie rozpoczęta dla programu .NET Framework 3.5. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="targeted-office-application"></a>Docelowe aplikacji pakietu Office  
 Po uaktualnieniu projektu pakietu Office do programu Visual Studio 2013, Visual Studio modyfikuje projekt pod kątem wersji pakietu Microsoft Office, który jest obsługiwany przez ten typ projektu, takie jak projektu dostosowania na poziomie dokumentu i projektów dodatku VSTO.  
  
 Projekty pakietu Office w Visual Studio 2013 można kierować [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplikacji. Visual Studio modyfikuje projekt pod kątem najnowszą wersję pakietu office, który został zainstalowany. Jeśli żaden z tych wersji pakietu Office są zainstalowane, program Visual Studio nie można uaktualnić projektu.  
  
> [!NOTE]  
>  Jeśli uaktualnienie projektów dodatku VSTO z docelowym [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] lub później, upewnij się, że `ThisAddIn_Startup` obsługi zdarzeń dodatku VSTO nie zawiera kodu, który uzyskuje dostęp do dokumentu w aplikacji. Aby uzyskać więcej informacji, zobacz [dostęp do dokumentu, podczas uruchamiania aplikacji pakietu Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Na poziomie dokumentu [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] Konwertuje dokumenty w projektach, które mają format binarny, takich jak dokumenty, które mają *xls* lub *doc* rozszerzenia do formatu pakietu Office Open XML. Aby uzyskać więcej informacji na temat Open XML, zobacz [wprowadzenie do nowych rozszerzeń nazw plików i Open XML formatuje](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).  
  
> [!NOTE]  
>  Tagi inteligentne nie są używane w 2010 programu Excel i Word 2010. W związku z tym jeśli rozwiązanie korzysta z tagami inteligentnymi, należy je usunąć przed rozpoczęciem testowania i debugowania go w programie Visual Studio 2013 lub Visual Studio 2015.  
  
## <a name="upgrade-microsoft-office-2003-projects"></a>Uaktualnianie projektów programu Microsoft Office 2003  
 Istnieje kilka dodatkowych kwestii dotyczących uaktualniania Dostosowywanie na poziomie dokumentu i dodatków VSTO, które odnoszą się do pakietu Microsoft Office 2003.  
  
### <a name="document-level-projects"></a>Projektów na poziomie dokumentu  
 Jeśli dokument projektu zawiera formanty formularzy systemu Windows, musi mieć również Visual Studio 2005 Tools dla drugiego wersji środowiska wykonawczego Office zainstalowany przed rozpoczęciem uaktualniania projektu. Jeśli ta wersja środowiska uruchomieniowego nie jest zainstalowany na komputerze dewelopera, przed rozpoczęciem uaktualniania projektu, uaktualnionym projekcie może zawierać kompilacji lub błędy wykonania. Po zakończeniu uaktualniania projektu, można odinstalować programu Visual Studio 2005 Tools for Office Runtime drugi w wersji z na komputerze deweloperskim, jeśli nie jest on używany przez innych rozwiązań pakietu Office. Ta wersja środowiska wykonawczego jest dostępna jako pakiet redystrybucyjny z Microsoft Download Center na [Microsoft Visual Studio 2005 Tools for Office Runtime Edition drugi (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
### <a name="vsto-add-in-projects"></a>Projektów dodatku VSTO  
 Jeśli plik rozwiązania dla oryginalnego projektu zawiera ustawienia lub InstallShield Limited Edition projekt, który został skonfigurowany do zainstalowania dodatku VSTO, Visual Studio uaktualnia projekt, ale nie powoduje żadnych dalszych zmian do projektu. Jeśli chcesz zachować przy użyciu pliku Instalatora systemu Windows do wdrożenia z dodatku VSTO, należy zmodyfikować projektu Instalatora lub InstallShield Limited Edition, aby zainstalować nowe wymagania wstępne, takie jak [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], programu Visual Studio 2010 Tools for Office Runtime oraz opcjonalnie podstawowe zestawy międzyoperacyjne odwołuje Twoje dodatku VSTO. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
 Jeśli chcesz używać ClickOnce do wdrażania dodatku VSTO z projektu Instalatora lub InstallShield Limited Edition można usunąć całkowicie. Aby uzyskać więcej informacji na temat wdrażania dodatków VSTO przy użyciu technologii ClickOnce, zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: rozwiązań uaktualniania pakietu Office](http://msdn.microsoft.com/en-us/a269e539-b717-4680-a568-2152b070347e)   
 [Migracja rozwiązań pakietu Office do programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Projekt uaktualnienia, opcje — Okno dialogowe](../vsto/project-upgrade-options-dialog-box.md)  
  
  