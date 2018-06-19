---
title: Debugowanie kontrolki ActiveX powiązania danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df11571bb1e37d458fd647ce1524f67432617b8f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474294"
---
# <a name="debugging-a-data-bound-activex-control"></a>Debugowanie kontrolki ActiveX powiązanego z danymi
Jeśli tworzysz formantu ActiveX, który zostanie powiązany do kontroli źródła danych można tworzyć aplikacji kontenera i debugowanie formantu ActiveX przy użyciu tego kontenera.  
  
 Można na przykład tworzenia aplikacji opartych na oknach dialogowych MFC i umieścić formantu powiązanego z danymi i kontroli źródła danych, w oknie dialogowym. Można użyć tej aplikacji MFC do czasu wykonywania testów oraz jako kontenera pliku wykonywalnego do debugowania formantu ActiveX powiązanego z danymi.  
  
## <a name="using-the-test-container"></a>Za pomocą kontenera testu  
 Kontener, który można łatwo zmodyfikować do obsługi różnych interfejsów albo formantu lub kontenera, należy użyć kontenera testu ActiveX jako plik wykonywalny dla sesji debugowania. W kontenerze testowym ActiveX kliknij **opcje** z **kontenera** menu, aby włączyć różnych interfejsów. Aby uzyskać więcej informacji, zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](/cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Aby wkraczać do kodu kontenera podczas debugowania, należy użyć wersji do debugowania z kontenera, lub użyj wersji do debugowania kontenera testu ActiveX. Aby uzyskać więcej informacji, zobacz [TSTCON próbki: Kontener testu formantu ActiveX](http://msdn.microsoft.com/en-us/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Zobacz też  
 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)   
 [Kontrolki ActiveX](/cpp/mfc/activex-controls)