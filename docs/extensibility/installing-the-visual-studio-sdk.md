---
title: Instalacja programu Visual Studio SDK | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8a5a4721eea178e4a9ab5766760ccf1405589684
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="installing-the-visual-studio-sdk"></a>Instalacja programu Visual Studio SDK
Visual Studio SDK jest opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalowanie programu Visual Studio SDK w ramach instalacji programu Visual Studio  
 Jeśli chcesz dołączyć VSSDK instalację programu Visual Studio, należy zainstalować **tworzenia rozszerzenia programu Visual Studio** obciążenia w obszarze **inne procesami**. Spowoduje to zainstalowanie programu Visual Studio SDK, a także wymagania wstępne. Dodatkowo można dostosować instalację, wybierając lub wyświetlanie unselecting składniki z podsumowania. 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalowanie programu Visual Studio SDK po zainstalowaniu programu Visual Studio  
 Jeśli zdecydujesz się zainstalować Visual Studio SDK po zakończeniu instalacji programu Visual Studio, uruchom ponownie Instalator programu Visual Studio i wybierz **tworzenia rozszerzenia programu Visual Studio** obciążenia.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalowanie programu Visual Studio SDK z rozwiązania  
 Po otwarciu rozwiązania z projektem rozszerzalności bez instalowania pierwszej VSSDK pojawi się monit przez pasek informacji wyróżnione powyżej Eksploratora rozwiązań. Powinien on wyglądać następująco:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalowanie programu Visual Studio SDK z poziomu wiersza polecenia  
Podobnie jak w przypadku programu Visual Studio obciążenia lub składnik, można także zainstalować element z wiersza polecenia. Zobacz [używania parametrów wiersza polecenia, aby zainstalować program Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) szczegółowe informacje dotyczące przełączników odpowiedni wiersz polecenia oraz sposobu określania identyfikatory składnika lub obciążenia.
  
 Należy pamiętać, że muszą używać Instalator programu Visual Studio, który odpowiada zainstalowanej wersji programu Visual Studio. Na przykład jeśli masz program Visual Studio Enterprise zainstalowanej na komputerze, możesz uruchomić Instalatora programu Visual Studio Enterprise (vs_enterprise.exe).