---
title: Opcjonalne Porównanie lokalnego folderu projektu do Store kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b6806a01127250b2376fee0aa77d55554eeba9bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681800"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Opcjonalne porównanie lokalnego folderu projektu do magazynu kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porównania folderu projektu do źródło kontroli Store](https://docs.microsoft.com/visualstudio/extensibility/internals/optional-comparison-of-local-project-folder-to-source-control-store).  
  
W źródle kontrolować 1.2 interfejsu API wtyczki porównania między lokalnym folderze projektu i kontrola źródła odbywa się za pomocą funkcji [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) i [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 W ramach **Eksploratora rozwiązań**, jeśli wybrano folderu zamiast pojedynczego pliku, **Porównaj wersje** menu skrótów wywołuje nowej [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) i [ SccDirDiff](../../extensibility/sccdirdiff-function.md) w wtyczka do kontroli źródła.  
  
## <a name="new-capability-flags"></a>Nowe flagi możliwości  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Nowe funkcje  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo` Funkcja jest wywoływana przed `SccDirDiff` do ustalenia, czy katalog roboczy jest pod kontrolą źródła. `SccDirDiff` Funkcja wyświetla różnice między bieżącym katalogu lokalnego i odpowiedni folder kontroli źródła. To polecenie pyta, czy wtyczka do kontroli źródła Aby wyświetlić listę zmian w katalogu. Wtyczka do kontroli źródła udostępnia własny interfejs użytkownika do wyświetlania różnic.  
  
> [!NOTE]
>  Ta funkcja używa tego samego flag poleceń jako [SccDiff](../../extensibility/sccdiff-function.md). Jako dostawca wtyczki kontroli źródła istnieje możliwość nie obsługuje operacji "szybkie diff" w przypadku katalogów.  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

