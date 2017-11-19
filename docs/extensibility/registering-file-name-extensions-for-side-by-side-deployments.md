---
title: "Rejestrowanie rozszerzeń nazw plików na potrzeby wdrożeń Side-By-Side | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 42c1c573554ee6d92b3967517bdcdf0f3106ce61
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Rejestrowanie rozszerzeń nazw plików na potrzeby wdrożeń Side-By-Side
VSPackages wdrożony w środowisku side-by-side, należy zarejestrować rozszerzeń nazw plików w celu skojarzenia plików z poprawną wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Jeśli nie używasz rozszerzenia nazwy pliku określonej wersji, rejestracja umożliwia użytkownikom Otwórz projekt i projektu plików z elementami w odpowiedniej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Temat rozszerzeń nazw plików](../extensibility/about-file-name-extensions.md)  
 W tym artykule omówiono sposób zarejestrowanych rozszerzeń nazw plików.  
  
 [Określanie obsługi pliku rozszerzenia nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Zawiera informacje o tym, jak zarejestrować aplikacji, które można otworzyć, edytowania i tak dalej, rozszerzenie nazwy pliku określonej.  
  
 [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md)  
 W tym artykule omówiono sposób rejestrowania zleceń.  
  
 [Zarządzanie skojarzeń plików Side-by-Side](../extensibility/managing-side-by-side-file-associations.md)  
 W tym artykule omówiono sposób obsługi urządzenia side-by-side, w których przypadku konkretnej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powinna być wywoływana w celu otwarcia pliku.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Obsługa wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 W tym artykule opisano problemy związane z wieloma wersjami [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i VSPackage podczas opracowywania i wdrażania dla użytkowników końcowych.