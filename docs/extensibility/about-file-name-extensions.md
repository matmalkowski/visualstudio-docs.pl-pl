---
title: "Temat rozszerzeń nazw plików | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8f504a70950ea9e808d50bd8b9bc7ef5dd92d699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="about-file-name-extensions"></a>Temat rozszerzeń nazw plików
Podczas rejestrowania rozszerzenia pliku pakiet VSPackage, należy ją skojarzyć z wersją [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Jest to ważne w przypadku więcej niż jedną wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest zainstalowany na komputerze.  
  
 Rozszerzenia plików do VSPackages są rejestrowane w kluczu HKEY_CLASSES_ROOT o wartości domyślne, wskazujące skojarzony identyfikator programowy (ProgID).  
  
 Poniżej przedstawiono przykład informacji o rejestracji dla rozszerzenia pliku .vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Pliki skojarzone z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] musi mieć określonej wersji ProgID, takich jak `VisualStudio.vcproj.8.0`, aby zezwolić side-by-side instalacji produktu do obsługi pliku rozszerzenia skojarzenia między wersjami. ProgID określonej wersji można też użyć zleceń standardowych, takich jak edytowanie otwarty i tak dalej, bez obawy, zastępowanie lub zastąpieniem przez inną aplikację lub wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 W niektórych przypadkach ProgID skojarzone z rozszerzeniem pliku nie powinna być zmieniana. Na przykład identyfikator ProgID dla rozszerzenia pliku .htm (progid = htmlfile) jest kodowany w wielu miejscach w systemie operacyjnym i jest powszechnie znane i używany w skojarzenie z pliki htm i HTML.  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestrowanie rozszerzeń nazw plików na potrzeby wdrożeń Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Określanie programów obsługi plików dla rozszerzeń nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md)