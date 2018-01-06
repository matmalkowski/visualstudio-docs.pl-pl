---
title: "Jaki &#39; s Nowość w źródle kontrolować wtyczka interfejsu API w wersji 1.3 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ac92c327a5eb4e51c7e6c22a73fb331843adc99f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Jaki &#39; s nowe w źródła formantu wtyczka interfejsu API wersji 1.3
API dodatku typu Plug-in kontroli źródła w wersji 1.3 wprowadza następujące nowe funkcje do zapewnienia bardziej zaawansowanych kontroli.  
  
## <a name="changes"></a>Zmiany  
 Nowe API dodatku typu Plug-in kontroli źródła w wersji 1.3 są następujące funkcje:  
  
|Funkcja|Omówienie|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Zezwala na dodatkowe możliwości usługi bits, należy podać|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Umożliwia badanie plików, które mają nowsze wersje w bazie danych kontroli wersji niż na dysku lokalnym|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Umożliwia badanie stanu zmiany nazwy (zmiana nazwy, dodatkami i usunięcia) dla określonych plików|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Umożliwia badanie katalogów i plików w bazie danych kontroli wersji|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Dodaje określony lista plików z bazy danych kontroli wersji do bieżącego projektu|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Wykonuje dyskretnej "Get" określonych plików (bez interfejsu użytkownika znajduje się)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Umożliwia dostęp do opcji specyficzne dla użytkownika|  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)