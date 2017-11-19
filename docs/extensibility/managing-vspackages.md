---
title: "Zarządzanie VSPackages | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55ba59a5a29181dfa3cdd70427720293582a648d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="managing-vspackages"></a>Zarządzanie VSPackages
W większości przypadków nie musisz martwić się o zarządzanie VSPackages, ponieważ szablonów projektów i elementów Zarejestruj i automatycznie załadować pakietu. Jednak w niektórych sytuacjach może być konieczne Dowiedz się więcej bit, aby można było zarządzać pakietu.  
  
## <a name="using-the-experimental-instance"></a>Przy użyciu eksperymentalne wystąpienie programu  
 Aby dowiedzieć się więcej na temat eksperymentalne wystąpienie, zobacz [eksperymentalne wystąpienie](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>VSPackages rejestrowania i wyrejestrowywania  
 Aby dowiedzieć się, jak rejestrowanie i wyrejestrowywanie pakiety VSPackage i inne typy rozszerzeń, zobacz [rejestrowanie i wyrejestrowywanie VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Ładowanie pakiet VSPackage  
 VSPackages można ustawić na automatyczne ładowanie podczas określonego identyfikatora GUID CMDUICONTEXT jest włączone. Aby uzyskać więcej informacji, zobacz [ładowania VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Przy użyciu AsyncPackage załadować VSPackages w tle  
 Klasa AsyncPackage umożliwia pakietu ładowania wątku w tle dla szybsza reakcja interfejsu użytkownika w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [porady: użycie AsyncPackage do VSPackages obciążenia w tle](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Kontekst opartego na regułach interfejsu użytkownika dla rozszerzenia  
 Konteksty interfejsu użytkownika opartego na regułach umożliwia autorom rozszerzenia zdefiniuj dokładne warunki kontekstu interfejsu użytkownika jest aktywny i załadować skojarzone VSPackages. Aby uzyskać więcej informacji, zobacz [porady: opartego na regułach Użyj kontekst interfejsu użytkownika dla rozszerzenia programu Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnosing-extension-performance"></a>Diagnozowanie rozszerzenia wydajności  
Rozszerzenia może wpłynąć na wydajność obciążenia uruchamiania i rozwiązania. Dowiedz się obliczania wpływ rozszerzenia programu Visual Studio i jak można ją analizować lokalnie Aby sprawdzić, czy rozszerzenie mogą być wyświetlane jako wydajności wpływające na rozszerzenia. Aby uzyskać więcej informacji, zobacz [porady: diagnozowanie wydajności rozszerzenia](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshooting-vspackages"></a>Rozwiązywanie problemów z VSPackages  
 Dowiedz się techniki rozwiązywania problemów VSPackages, które nie są ładowane lub występują błędy: [VSPackages Rozwiązywanie problemów](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Zobacz też  
 [VSPackages](../extensibility/internals/vspackages.md)