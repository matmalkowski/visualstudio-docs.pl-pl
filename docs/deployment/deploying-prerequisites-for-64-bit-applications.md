---
title: Wdrażanie wstępnie wymaganych składników dla 64-bitowych aplikacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed3ffb52e73be1f86b9ae4be67d130807fc7e238
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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
 [Aplikacje 64-bitowe](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)