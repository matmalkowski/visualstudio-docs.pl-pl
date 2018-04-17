---
title: Kompilowanie rozwiązań pakietu Office | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1b01a00cec5bc02d9605d41aa961b6ecd18196f1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="building-office-solutions"></a>Kompilowanie rozwiązań pakietu Office
  Ogólnie rzecz biorąc kompilowanie i debugowanie projektów pakietu Office jest taka sama jak kompilowanie i debugowanie innych typów projektów programu Visual Studio, takie jak formularze systemu Windows. W tematach w tej sekcji opisano różnice, które istnieją. Aby uzyskać ogólne informacje o sposobie tworzenia aplikacji, zobacz [kompilowania i tworzenia w programie Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
## <a name="project-output-for-office-projects"></a>Dane wyjściowe projektu dla projektów pakietu Office  
 Lokalizacja danych wyjściowych dla projektów pakietu Office jest *projectname*\bin\release lub *projectname*\bin\debug. Nie można utworzyć katalogu wdrożenia.  
  
### <a name="document-level-projects"></a>Projektów na poziomie dokumentu  
 Podczas kompilowania projektu poziomie dokumentu następujące elementy są uwzględnione w danych wyjściowych projektu:  
  
-   Kopię dokumentu projektu.  
  
-   Projekt zestawu i wszystkich przywoływanych zestawów, które mają ich **Kopiuj lokalnie** ustawioną właściwość **true**.  
  
-   Manifest aplikacji zawiera manifest rozszerzenia nazwy pliku. Aby uzyskać więcej informacji, zobacz [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
-   Manifest rozmieszczenia ma .vsto rozszerzenia nazwy pliku. Aby uzyskać więcej informacji, zobacz [manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Plik programu (PDB) bazy danych.  
  
> [!NOTE]  
>  W przypadku tworzenia rozwiązania poziomie dokumentu do zdalnej lokalizacji zamiast komputera lokalnego, Dodaj pełną ścieżkę do listy zaufanych lokalizacji w Centrum zaufania aplikacji. Aby uzyskać więcej informacji, zobacz sekcję o nazwie udzielanie zaufania do dokumentów w [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md).  
  
### <a name="application-level-projects"></a>Projektów na poziomie aplikacji  
 Podczas tworzenia projektów dodatku VSTO następujące elementy są uwzględnione w danych wyjściowych projektu:  
  
-   Projekt zestawu i wszystkich przywoływanych zestawów, które mają ich **Kopiuj lokalnie** ustawioną właściwość **true**.  
  
-   Manifest aplikacji zawiera manifest rozszerzenia nazwy pliku. Aby uzyskać więcej informacji, zobacz [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
-   Manifest rozmieszczenia ma .vsto rozszerzenia nazwy pliku. Aby uzyskać więcej informacji, zobacz [manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Plik bazy danych (PDB) programu dla zestawu projektu.  
  
 Proces kompilacji dla projektów dodatku VSTO również tworzy zbiór wpisów rejestru na komputerze dewelopera, które są wymagane do załadowania dodatku VSTO. Aby uzyskać więcej informacji, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 W przypadku tworzenia projektów dodatku VSTO dla programu Outlook zawierający regionów formularzy, proces kompilacji dodaje następujące dodatkowe informacje w rejestrze:  
  
-   Klucz dla każdej klasy wiadomości, który jest skojarzony z co najmniej jeden regionów formularzy.  
  
-   Wpis dla każdego regionu formularza i skojarzona wartość, która reprezentuje nazwę dodatku VSTO dla programu Outlook.  
  
 Program Outlook musi tych informacji, aby załadować regionów formularzy.  
  
## <a name="referenced-assemblies"></a>Zestawy, do których istnieją odwołania  
 Zestawy (projektów biblioteki klas w tym) można odwoływać się z projektu kompilowanie rozwiązań pakietu Office. Każdy zestaw z odwołania ma właściwość o nazwie **Kopiuj lokalnie**. **Kopiuj lokalnie** wskazuje, czy zestaw jest kopiowany do katalogu wyjściowego. Domyślnie jest ustawiona wartość **true**. Każdy przywoływanego zestawu, który ma **Kopiuj lokalnie** ustawioną **true** jest kopiowany do katalogu wyjściowego.  
  
## <a name="security-during-the-build-process"></a>Zabezpieczeń podczas procesu kompilacji  
 Visual Studio automatycznie konfiguruje ustawienia zabezpieczeń na komputerze dewelopera udzielenia zaufania do rozwiązania podczas procesu kompilacji. Umożliwia to rozwiązanie do uruchomienia podczas jego debugowania.  
  
 Projekty Office używają certyfikatów do weryfikowania wydawcy. Visual Studio automatycznie tworzy tymczasowy certyfikat, aby zidentyfikować rozwiązań pakietu Office i konfiguruje na komputerze deweloperskim ufać certyfikatowi tymczasowego.  
  
 Aby uzyskać więcej informacji, zobacz [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md).  
  
### <a name="network-projects"></a>Projekty sieci  
 W przypadku zestawu lub dokument w lokalizacji w udziale sieciowym, aktualizacji zasady zabezpieczeń lokalnych (na poziomie użytkownika) nie jest wystarczająco, aby umożliwić uruchomienie rozwiązania. Administrator musi przyznać pełne zaufanie na poziomie komputera do zestawów i dokumentów, które są w udziale sieciowym, zanim rozwiązanie będzie uruchamiany. Aby uzyskać więcej informacji na temat sposobu ustawiania zasad zabezpieczeń, zobacz [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md).  
  
 Dla projektów na poziomie dokumentu należy dodać pełną lokalizację dokumentu do listy zaufanych folderów pakietu Office. Aby uzyskać więcej informacji, zobacz [udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
## <a name="changing-the-platform-target"></a>Zmiana platformy docelowej  
 Domyślnie jest docelowej platformy dla projektów pakietu Office **Any CPU**. Zwykle nie należy zmieniać tego ustawienia. Rozwiązania pakietu Office, które są tworzone za **Any CPU** platformy docelowej ustawienie uruchomienia w 32-bitowe i 64-bitowych wersjach systemu Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] lub [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
 Platformy docelowej x64 należy ustawić tylko wtedy, gdy tworzysz rozwiązania, które będą uruchamiane tylko w 64-bitowe wersje programu Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] lub [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], i rozwiązania wywołań natywnych interfejsów API 64-bitowych. Aby uzyskać więcej informacji na temat zmiany ustawień platformy docelowej zobacz [porady: Konfigurowanie projektów do platform docelowych](../ide/how-to-configure-projects-to-target-platforms.md).  
  
 Jeśli ustawisz x64 docelowej platformy rozwiązania nie zostanie uruchomiony w 32-bitowe wersje systemu Windows lub pakietu Office. X64 platformy docelowej wymaga rozwiązania do uruchamiania w procesie 64-bitowych.  
  
## <a name="using-the-clean-command"></a>Za pomocą polecenia Clean  
 Aby usunąć pliki skompilowanym projektem z na komputerze deweloperskim, można użyć **wyczyść** na **kompilacji** w menu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. **Wyczyść** polecenie usuwa wszystkie pliki w lokalizacji danych wyjściowych kompilacji. Dla projektów na poziomie aplikacji **wyczyść** polecenia również usuwa wpisy z rejestru, które są tworzone przez proces kompilacji.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Debugowanie projektów pakietu Office](../vsto/debugging-office-projects.md)|Przedstawia informacje o zagadnieniach dotyczących debugowanie projektów pakietu Office.|  
|[Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Przedstawia sposób tworzenia podstawowego dostosowywania poziomie dokumentu dla programu Excel.|  
|[Instrukcje: Ponowne włączanie wcześniej wyłączonego dodatku narzędzi VSTO](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Opisuje sposób ponownie włączyć dodatku VSTO twarde lub soft wyłączono.|  
|[Projektowanie i tworzenie rozwiązań Office](../vsto/designing-and-creating-office-solutions.md)|Zawiera linki do informacji o tworzeniu rozwiązań pakietu Office i informacji na temat roli zestawów w rozwiązaniu.|  
  
  