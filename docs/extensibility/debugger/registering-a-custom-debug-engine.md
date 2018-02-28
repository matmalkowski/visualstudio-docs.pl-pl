---
title: Rejestrowanie niestandardowe aparatu debugowania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 50903d9b45828725da03c0fcb0db0f08d7f884eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="registering-a-custom-debug-engine"></a>Aparat debugowania niestandardowego rejestrowania
Aparat debugowania musi zarejestrować się jako fabryki klasy COM zgodne z konwencjami jak również zarejestrować w usłudze Visual Studio za pomocą podklucza rejestru programu Visual Studio.  
  
> [!NOTE]
>  Przykład sposobu rejestrowania aparat debugowania można znaleźć w przykładowym TextInterpreter jest utworzone jako część [samouczek: tworzenie debugowania aparatu za pomocą biblioteki ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Proces serwera biblioteki DLL  
 Zazwyczaj aparat debugowania jest zaimplementowana w jego własnej biblioteki DLL jako serwer COM. Oznacza to, że aparat debugowania należy zarejestrować CLSID jego fabryki klasy COM przed Visual Studio do niego dostęp. Aparat debugowania musi zarejestrować się z programem Visual Studio się w celu ustalenia żadnych właściwości (w przeciwnym razie nazywane metryk) debugowania, a następnie aparat obsługuje. Wybór metryki, które są zapisywane w podkluczu rejestru programu Visual Studio dla aparatu debugowania, zależy od funkcje, które obsługuje aparat debugowania.  
  
 [Pomocnicy zestawu SDK dla debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) opisuje nie tylko w lokalizacji rejestru należy zarejestrować aparatu debugowania; biblioteki dbgmetric.lib, która zawiera liczbę przydatne funkcje i deklaracje dla deweloperów języka C++, które opisano również manipulowanie łatwiejsze rejestru.  
  
### <a name="example"></a>Przykład  
 Przykład typowej (z próbki TextInterpreter) przedstawiająca sposób używania `SetMetric` funkcji (z dbgmetric.lib), aby zarejestrować aparat debugowania z programem Visual Studio. Metryki przekazywany również są definiowane w dbgmetric.lib.  
  
> [!NOTE]
>  TextInterpreter jest aparat debugowania podstawowego; nie implementuje — i w związku z tym nie rejestruje — wszelkich innych funkcji. Bardziej szczegółowy aparat debugowania musi całą listę `SetMetric` wywołania lub ich odpowiedniki obsługuje jeden dla każdej funkcji aparat debugowania.  
  
```  
// Define base registry subkey to Visual Studio.  
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";  
  
HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)  
{  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);  
  
    return base::RegisterServer(bRegTypeLib, pCLSID);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aparat debugowania niestandardowych](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Pomocnicy zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Samouczek: Tworzenie aparat debugowania, za pomocą biblioteki ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)