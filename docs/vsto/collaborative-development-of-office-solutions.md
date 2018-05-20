---
title: Programowanie zespołowe rozwiązań pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9bf85dd1ba39df35e337f1b6b80099e3d5bcd774
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="collaborative-development-of-office-solutions"></a>Programowanie zespołowe rozwiązań pakietu Office
  Wiele deweloperzy mogą pracować w projekcie pakietu Office w taki sam sposób jak Użytkownicy współpracujący do innych projektów programu Visual Studio. Visual Studio poprawnie lokalizuje instalacji pakietu Microsoft Office na każdym komputerze, nawet jeśli pakiet Office jest zainstalowany w różnych lokalizacjach. Istnieją pewne istotne kwestie, którymi należy się zapoznać.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Debugowanie właściwości nie są udostępnione.  
 Debugowanie właściwości nie są współużytkowane przez wielu użytkowników pod kontrolą źródła. Projekty Visual Basic i Visual C# przechowywane właściwości debugowania w pliku specyficzne dla użytkownika (*ProjectName*. vbproj.user lub *ProjectName*. csproj.user), a ten plik nie jest pod kontrolą źródła. W przypadku debugowania jest więcej niż jedna osoba, każda osoba właściwości debugowania ręcznie wprowadzić.  
  
 Jeśli projekt jest przechowywany w udziale sieciowym, a nie w kontroli źródła, kilka dodatkowych czynności należy brać producentów Otwórz rozwiązanie i zestawu testów.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Kontrola źródła wymaga wyewidencjonowania wszystkie pliki  
 Jeśli używasz kontroli źródła dla projektów, należy sprawdzić się wszystkie pliki w pliku kodu w **Eksploratora rozwiązań** (takich jak *ThisDocument*, *ThisWorkbook*, lub *Thisaddin —* kodu plików) przy każdej zmianie pliku kodu, nawet te pliki, które są domyślnie ukryte. Jeśli wyewidencjonować plik kodu najwyższego poziomu, zmiany mogą zostać utracone.  
  
 Po wprowadzeniu zmian, sprawdź, czy wszystkie pliki ponownie. Aby uzyskać więcej informacji o plikach ukrytych kodu w projektach, zobacz [projektów pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Zabezpieczenia nieformalne współpracy w sieci  
 Dla wszystkich rozwiązań poziomie dokumentu, które znajdują się w lokalizacji sieciowej (takie jak \\ \\ *Servername*\\*Sharename*), pełny lokalizacji musi zostać dodany do Lista zaufanych folderu w aplikacji Microsoft Office, w którym pracujesz. Wybierz opcję, aby dołączyć podkatalogów w folderze głównym lub specjalnie dodać debugowania i tworzenie folderów, do listy zaufanych folderów. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [przyznać zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
 Certyfikaty tymczasowe, które są automatycznie generowane w czasie kompilacji nie są zabezpieczane przez hasła. Certyfikaty zawierają nazwę logowania dewelopera i innych danych osobowych. Jeśli wdrożono dostosowania, które są podpisane przez certyfikaty tymczasowe, inne można dostęp do tych informacji.  
  
## <a name="see-also"></a>Zobacz także  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)  
  
  