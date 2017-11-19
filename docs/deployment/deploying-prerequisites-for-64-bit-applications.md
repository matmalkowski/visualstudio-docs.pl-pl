---
title: "Wdrażanie wstępnie wymaganych składników dla 64-bitowych aplikacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: aefb619487fba984e8f625dfe414c2f514f28c70
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych
Wdrożenie ClickOnce obsługuje instalacji aplikacji na platformach 64-bitowych. Platformy docelowe są **x86** dla 32-bitowych platform **x64** obsługi zestawów instrukcji AMD64 i EM64T maszyn i **Itanium** dla 64-bitowego procesora Itanium.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Poniższa tabela zawiera listę pakietów redystrybucyjnych, których mogą używać jako wymagania wstępne dla instalacji aplikacji 64-bitowych.  
  
 Jeśli wybierzesz wymagania wstępne, które nie są zainstalowane składniki 64-bitowych, może zostać wyświetlony z ostrzeżeniem, że wybrane pakiety nie są dostępne dla platformy 64-bitowej.  
  
|Pakiet redystrybucyjny|obsługuje x64|Obsługa IA64|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|Tak|Nie|  
|Visual C++ 2010 środowiska uruchomieniowego bibliotek (IA64)|Nie|Tak|  
|Visual C++ 2010 środowiska uruchomieniowego Libriaries (x64)|Tak|Nie|  
|Microsoft .NET Framework 4 (x86 i x64)|Tak||  
|Program Microsoft .NET Framework 4 Client Profile (x86 i x64)|Tak||  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md)   
 [Porady: Instalowanie wymagań wstępnych za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64-bit — aplikacje](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)