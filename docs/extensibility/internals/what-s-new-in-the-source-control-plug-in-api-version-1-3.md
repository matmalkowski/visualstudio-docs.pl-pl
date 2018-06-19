---
title: Co&#39;s Nowość w źródle kontrolować wtyczka interfejsu API w wersji 1.3 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: abeb2a0a936a5d706e2e3744e9dd0f4e3123bdbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31145012"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Co&#39;s Nowość w źródle kontrolować wtyczka interfejsu API w wersji 1.3
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