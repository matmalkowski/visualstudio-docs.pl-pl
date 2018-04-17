---
title: Implementacja dostawcy portu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0743f307dc579f6197880b0b89acaf2db0dda08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-a-port-supplier"></a>Implementacja dostawcy portu
Dostawca portu udostępnia porty na żądanie do menedżera sesji debugowania (SDM). Dostawca portu musi wykonywane podczas debugowania na maszynę z systemem innym niż DCOM lub gdy nowe urządzenie musi być obsługiwany. Na przykład aby umożliwić debugowanie na telefon komórkowy, może implementować dostawcy port udostępniający nawiązać połączenia z telefonem komórkowym (być może przy użyciu IR lub połączenie komórki) i wylicza procesy i programy uruchomione na telefonie porty.  
  
 W przypadku debugowania programów na komputerach z systemem Windows (w tym zdalnego debugowania) programu Visual Studio udostępnia dostawców portu dla macierzystego i procesy środowiska uruchomieniowego języka wspólnego (CLR), nie istnieje potrzeba do implementowania dostawcy portu w takich przypadkach.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie i rejestrowanie dostawcy portu](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 W tym artykule omówiono, jak SDM współdziała z portu dostawcy i jego portów.  
  
 [Wymagane interfejsy dostawcy portów](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Dokumenty interfejsów, które muszą zostać zaimplementowane uzyskać portu dostawcy.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 Zawiera opis głównych pojęć architektury debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)