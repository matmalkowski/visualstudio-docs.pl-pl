---
title: "Porównanie folderu projektu do kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cde0a7c34fe81c86d9f500bb1800006e5291ee92
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Nowości w źródła formantu wtyczka interfejsu API wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)