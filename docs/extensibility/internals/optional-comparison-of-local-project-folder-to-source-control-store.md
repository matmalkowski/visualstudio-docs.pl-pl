---
title: Porównanie folderu projektu do kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e0f6f2185385ee7ec3942556a43f58d43e7a4da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130575"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Opcjonalne porównanie Folder lokalny projekt do kontroli źródła
W źródle kontrolować 1.2 interfejsu API wtyczek porównania folder lokalny projektu z kontroli źródła odbywa się za pomocą funkcji [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) i [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 W ramach **Eksploratora rozwiązań**, jeśli wybrano folder zamiast pliku poszczególnych **Porównaj wersje** menu skrótów wywołuje nowe [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) i [ SccDirDiff](../../extensibility/sccdirdiff-function.md) w wtyczkę kontroli źródła.  
  
## <a name="new-capability-flags"></a>Nowe możliwości flagi  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Nowe funkcje  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo` Funkcja jest wywoływana przed `SccDirDiff` do ustalenia, czy katalog roboczy jest pod kontrolą źródła. `SccDirDiff` Funkcja przedstawia różnice między bieżącym katalogu lokalnego i odpowiedniego folderu kontroli źródła. To polecenie zapyta wtyczka do kontroli źródła Aby wyświetlić listę zmian w katalogu. Wtyczka do kontroli źródła udostępnia własnego interfejsu użytkownika, aby wyświetlić różnice.  
  
> [!NOTE]
>  Ta funkcja korzysta z tej samej flagi polecenie jako [SccDiff](../../extensibility/sccdiff-function.md). Jako dostawca wtyczkę kontroli źródła możesz nie obsługuje operacji "szybkie różnicowego" dla katalogów.  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)