---
title: "Wyłącz ostrzeżenia dotyczące zgodności dla plug-in kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 622c0d4a75289e5025051b339b959a6b0b56442d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Porady: wyłączanie ostrzeżenia dotyczące zgodności dla plug-in kontroli źródła
Użytkownik może zobaczyć kilka ostrzeżenia dotyczące zgodności przy kontroli źródła w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Ostrzeżenia przedstawione zależą od możliwości wtyczkę kontroli źródła i być wyłączona, ponieważ szczegółowe tutaj.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Aby wyłączyć ostrzeżenia: "Aby zapewnić optymalną integracją kontroli źródła z programem Visual Studio..."  
  
-   Ustaw następujący wpis rejestru (Dodawanie wartość, jeśli to konieczne):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001  
  
     To ostrzeżenie jest wyświetlane dla wszystkich innych niż -[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] dodatków plug-in.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Aby wyłączyć ostrzeżenia: "zainstalowany dostawca kontroli źródła nie wspiera wszystkich możliwości..."  
  
-   Ustaw następujące wartości rejestru dwa (Dodawanie wartości, jeśli to konieczne):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001  
  
     To ostrzeżenie jest wyświetlane, jeśli wtyczka do kontroli źródła nie jawnie obsługuje ponowne wejście dla wielu projektów (jeśli można sprawdzić w tylko jednym pliku, a projekt w czasie).  
  
     Najlepiej obsługuje ponowne wejście (`SCC_CAP_REENTRANT` możliwości); spowoduje to usunięcie tego ostrzeżenia. Jednak jeśli ta obsługa nie jest możliwe, można ustawić te wpisy rejestru.  
  
## <a name="see-also"></a>Zobacz też  
 [Flagi możliwości](../extensibility/capability-flags.md)