---
title: Za pomocą Menedżera tekstu do monitorowania ustawień globalnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e6c61a6859a2e8d359b2185ce959aa941944380f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Za pomocą Menedżera tekstu do monitorowania ustawień globalnych
W przypadku zastosowania edytora core, należy monitorować zmiany wprowadzone w ustawieniach globalnych, ponieważ te zmiany mogą wpłynąć na wystąpienie edytora. Można śledzić zmiany przez nasłuchiwanie zdarzeń zgłaszanych przez Menedżera tekstu. Na przykład po określeniu globalne preferencji wygląd i zachowanie składnika w edytorze podstawowe, takie jak jego obiekt danych dokumentu Menedżera tekstu przechowuje te informacje i przesyła je do wszystkich klientów, których dotyczy.  
  
## <a name="text-manager-functions"></a>Funkcje Menedżera tekstu  
 Menedżer tekstu informuje o zdarzeniach dla wielu ustawień, takich jak następujące:  
  
-   Określa, czy bufor jest pod kontrolą kodu źródłowego  
  
-   Jak zarejestrować powiadomienia o zmianach pliku  
  
-   Jak do śledzenia widoków, które są skojarzone z niektórych buforów  
  
-   Tekstu kolorowania preferencji  
  
-   Karta i preferencje miejsca  
  
 Preferencje, które są unikatowe dla danego języka nie są zarządzane przez Menedżera tekstu. Te ustawienia muszą być zarządzane przez usługę każdego języka.  
  
 Powiadamianie o zdarzeniach dla Menedżera tekstu jest zapewniana przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interfejsu. Implementuje ten interfejs na komputerze klienckim obiektu do obsługi zdarzenia wywoływane Menedżera tekstu. Zarejestruj te zdarzenia za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfejsu na Menedżera tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [W edytorze Core](../extensibility/inside-the-core-editor.md)   
 [Funkcje edycji](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)