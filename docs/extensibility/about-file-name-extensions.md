---
title: Temat rozszerzeń nazw plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fd181bb7daca21ff263dcb7989a0aecbef3ed278
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081699"
---
# <a name="about-file-name-extensions"></a>Temat rozszerzeń nazw plików
Po zarejestrowaniu rozszerzenie pliku pakietu VSPackage, należy ją skojarzyć z wersją [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Jest to ważne, jeśli więcej niż jedna wersja [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest zainstalowany na komputerze.  
  
 Rozszerzenia plików dla pakietów VSPackage są zarejestrowane w obszarze **HKEY_CLASSES_ROOT** klucza z wartością domyślną, który wskazuje na skojarzony identyfikator programowy (ProgID).  
  
 W poniższym przykładzie przedstawiono informacje o rejestracji dla *.vcproj* rozszerzenie pliku:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Plików skojarzonych z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] musi mieć określonej wersji ProgID, takich jak `VisualStudio.vcproj.8.0`. Numerów wersji ProgID umożliwia instalacje side-by-side produktu do utrzymania skojarzenia rozszerzeń plików między wersji produktu. ProgID specyficzny dla wersji pozwala również na używanie zleceń standardowych, takie jak edytowanie otwarte i tak dalej, bez obawy, zastępowanie lub zastąpieniem przez inne aplikacje lub wersje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 W niektórych przypadkach także identyfikator ProgID skojarzone z rozszerzeniem pliku nie powinna być zmieniana. Na przykład identyfikatora programu *.htm* rozszerzenie pliku (progid = htmlfile) jest ustalony w wielu miejscach w systemie operacyjnym, a jest powszechnie znane i używane w połączeniu z *.htm* i *.html* plików.  
  
## <a name="see-also"></a>Zobacz także  
 [Rejestrowanie rozszerzeń nazw plików dla wdrożeń side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Określanie programów obsługi plików dla rozszerzeń nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md)