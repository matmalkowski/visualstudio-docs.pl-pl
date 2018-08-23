---
title: Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 0f98a611b382f3884ede2e1e239944b9e584ab77
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678351"
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wdrażanie wymagania wstępne dla aplikacji 64-bitowych](https://docs.microsoft.com/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications).  
  
Wdrożenie ClickOnce obsługuje instalację aplikacji na platformach 64-bitowych. Platformy docelowe są **x86** dla platform 32-bitowych **x64** obsługi zestawów instrukcji AMD64 oraz obsługą technologii EM64T maszyn i **Itanium** dla procesora Itanium 64-bitowych.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Poniższa tabela zawiera listę pakietów redystrybucyjnych, używanego jako wymagania wstępne dotyczące instalacji aplikacji 64-bitowych.  
  
 Jeśli wybierzesz wstępnie wymaganego składnika, który nie ma 64-bitowych składników, może zostać wyświetlony z ostrzeżeniem, że wybrane pakiety nie są dostępne dla platformy 64-bitowych.  
  
|Pakiet redystrybucyjny|obsługuje x64|Obsługa IA64|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../includes/vsto-runtime-md.md)]|Tak|Nie|  
|Biblioteki Visual C++ 2010 Runtime (IA64)|Nie|Tak|  
|Visual C++ 2010 Runtime Libriaries (x64)|Tak|Nie|  
|Microsoft .NET Framework 4 (x86 i x64)|Tak||  
|Microsoft .NET Framework 4 Client Profile (x86 i x64)|Tak||  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md)   
 [Porady: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Aplikacje 64-bitowe](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)



