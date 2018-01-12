---
title: "Programowanie zespołowe rozwiązań pakietu Office | Dokumentacja firmy Microsoft"
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
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3b69eccc3f6c140c44bff3b2d3d24e33914cae84
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="collaborative-development-of-office-solutions"></a>Programowanie zespołowe rozwiązań pakietu Office
  Wiele deweloperzy mogą pracować w projekcie pakietu Office w taki sam sposób jak Użytkownicy współpracujący do innych projektów programu Visual Studio. Visual Studio poprawnie lokalizuje instalacji pakietu Microsoft Office na każdym komputerze, nawet jeśli pakiet Office jest zainstalowany w różnych lokalizacjach. Istnieją pewne istotne kwestie, którymi należy się zapoznać.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Debugowanie właściwości nie są udostępnione.  
 Debugowanie właściwości nie są współużytkowane przez wielu użytkowników pod kontrolą źródła. Projekty Visual Basic i Visual C# przechowywane właściwości debugowania w pliku specyficzne dla użytkownika (*ProjectName*. vbproj.user lub *ProjectName*. csproj.user), a ten plik nie jest pod kontrolą źródła. W przypadku debugowania jest więcej niż jedna osoba, każda osoba właściwości debugowania ręcznie wprowadzić.  
  
 Jeśli projekt jest przechowywany w udziale sieciowym, a nie w kontroli źródła, kilka dodatkowych czynności należy brać producentów Otwórz rozwiązanie i zestawu testów.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Kontrola źródła wymaga wyewidencjonowania wszystkie pliki  
 Jeśli używasz kontroli źródła dla projektów, należy sprawdzić się wszystkie pliki w pliku kodu w **Eksploratora rozwiązań** (takich jak pliki kodu ThisDocument, ThisWorkbook lub klasy ThisAddIn) przy każdej zmianie pliku kodu nawet pliki, które są domyślnie ukryte. Jeśli wyewidencjonować plik kodu najwyższego poziomu, zmiany mogą zostać utracone.  
  
 Po wprowadzeniu zmian, sprawdź, czy wszystkie pliki ponownie. Aby uzyskać więcej informacji o plikach ukrytych kodu w projektach, zobacz [projekty pakietu Office w Visual Studio środowiska](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Zabezpieczenia nieformalne współpracy w sieci  
 Dla wszystkich rozwiązań poziomie dokumentu, które znajdują się w lokalizacji sieciowej (takie jak \\ \\ *Servername*\\*Sharename*), pełny lokalizacji musi zostać dodany do Lista zaufanych folderu w aplikacji Microsoft Office, w którym pracujesz. Wybierz opcję, aby dołączyć podkatalogów w folderze głównym lub specjalnie dodać debugowania i tworzenie folderów, do listy zaufanych folderów. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
 Certyfikaty tymczasowe, które są automatycznie generowane w czasie kompilacji nie są zabezpieczane przez hasła. Certyfikaty zawierają nazwę logowania dewelopera i innych danych osobowych. Jeśli wdrożono dostosowania, które są podpisane przez certyfikaty tymczasowe, inne można dostęp do tych informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md)  
  
  