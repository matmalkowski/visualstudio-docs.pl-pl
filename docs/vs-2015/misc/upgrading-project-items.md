---
title: Uaktualnianie elementy projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: douge
ms.openlocfilehash: 10005b38f01c3cad97cf8c7aab391e4546737295
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682262"
---
# <a name="upgrading-project-items"></a>Uaktualnianie elementów projektu
W przypadku dodania lub zarządzania elementami wewnątrz systemy projektu, który nie należy implementować, konieczne może uczestniczyć w procesie uaktualniania projektu. Crystal Reports znajduje się przykład elementu, który można dodać do systemu projektu.  
  
 Zazwyczaj chcesz wykorzystać już w pełni utworzona i uaktualnionego projektu, ponieważ muszą wiedzieć, jakie są odwołania do projektu i jakie inne właściwości projektu są podejmowanie decyzji uaktualnienia implementacji elementu projektu.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Aby uzyskać powiadomienia o uaktualnieniu projektu  
  
1.  Ustaw <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> flagi (zdefiniowanymi w vsshell80.idl) w danej implementacji elementu projektu. Powoduje to, że element projektu pakietu VSPackage, można automatycznie załadować, kiedy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] powłoki Określa, czy system projektu trwa uaktualnianie.  
  
2.  Aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfejsu za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> metody.  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Interfejsu jest uruchamiany po implementacji systemu projektu został wykonany jego operacji uaktualnienia, a następnie jest tworzony nowy projekt uaktualniony. W zależności od scenariusza <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfejsu jest wyzwalane po <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metody.  
  
### <a name="to-upgrade-the-project-item-files"></a>Aby uaktualnić plików elementów projektów  
  
1.  Należy rozważnie zarządzać procesu tworzenia kopii zapasowej plików w danej implementacji elementu projektu. W szczególności dotyczy to usługi kopii zapasowej side-by-side, gdzie `fUpgradeFlag` parametru <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> ustawiono metodę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, gdzie pliki, które miały utworzone kopie zapasowe są umieszczane na stronie pliki, które są oznaczone jako ".old". Kopie zapasowe plików starszych niż czas systemowy, gdy został uaktualniony projekt może być wyznaczony jako nieaktualne. Ponadto one mogą zostać zastąpione, jeśli należy podjąć specjalne kroki, aby zapobiec takiej sytuacji.  
  
2.  W tym czasie element projektu pobiera powiadomienie z informacją o uaktualnieniu projektu **Kreator konwersji Visual Studio** jest nadal wyświetlany. Dlatego należy używać metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfejsu, aby zapewnić uaktualnienia wiadomości do Kreatora interfejsu użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator konwersji Visual Studio](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Uaktualnianie projektów niestandardowych](../misc/upgrading-custom-projects.md)