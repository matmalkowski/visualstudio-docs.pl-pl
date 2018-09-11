---
title: Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 10a5883e655fc5ee8a37bbe61f531b6b266ebb55
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281898"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych
Wdrożenie ClickOnce obsługuje instalację aplikacji na platformach 64-bitowych. Platformy docelowe są **x86** dla platform 32-bitowych **x64** obsługi zestawów instrukcji AMD64 oraz obsługą technologii EM64T maszyn i **Itanium** dla procesora Itanium 64-bitowych.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Poniższa tabela zawiera listę pakietów redystrybucyjnych, używanego jako wymagania wstępne dotyczące instalacji aplikacji 64-bitowych.  
  
 Jeśli wybierzesz wstępnie wymaganego składnika, który nie ma 64-bitowych składników, może zostać wyświetlony z ostrzeżeniem, że wybrane pakiety nie są dostępne dla platformy 64-bitowych.  
  
|Pakiet redystrybucyjny|obsługuje x64|Obsługa IA64|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|Tak|Nie|  
|Biblioteki Visual C++ 2010 Runtime (IA64)|Nie|Tak|  
|Biblioteki Visual C++ 2010 Runtime (x64)|Tak|Nie|  
|Microsoft .NET Framework 4 (x86 i x64)|Tak||  
|Microsoft .NET Framework 4 Client Profile (x86 i x64)|Tak||  
  
## <a name="see-also"></a>Zobacz także  
 [Wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md)   
 [Porady: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [aplikacje 64-bitowe](/dotnet/framework/64-bit-apps)