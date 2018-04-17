---
title: Ciągi używane jako klucze do znajdowania wtyczka do kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a42eebe67ce1f611cf6e48883bc09139f241e658
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Ciągi używane jako klucze do znajdowania wtyczka do kontroli źródła
Klucze do uzyskiwania dostępu do rejestru, aby znaleźć informacje o kontroli źródła wtyczek są następujące ciągi.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, i `STR_SCCPROVIDERNAME` kluczy rejestru i wartości używane do rejestrowania biblioteki DLL jako wtyczka do kontroli źródła dla programu Visual Studio.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, i `SCC_STATUS_FILE` służą do opisywania formatu MSSCCPRJ. Plik SCC.  
  
## <a name="string-keys-and-values"></a>Ciąg kluczy i wartości  
  
|Key|Wartość|  
|---------|-----------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|SCCServerPath|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|Kontroli kodu źródłowego|  
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|  
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|  
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|  
|`SCC_STATUS_FILE`|MSSCCPRJ. SCC|  
|`SCC_KEY`|SCC|  
|`SCC_FILE_SIGNATURE`|Pliku kontroli kodu źródłowego|  
|`SCC_NSE`|Rozszerzenie Namespace|  
|`SCC_NSE_PREFIX`|Prefiks Protokół|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|  
  
## <a name="see-also"></a>Zobacz też  
 [Plug-in kontroli źródła](../extensibility/source-control-plug-ins.md)   
 [Porady: Instalowanie dodatku Plug-in kontroli źródła](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)