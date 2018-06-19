---
title: EXCEPTION_STATE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1faa847d907af938bb5f91206a5f438bcba886a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104907"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
Określa stan wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```csharp  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 EXCEPTION_NONE  
 Nie zostanie zatrzymana na wyjątek.  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 Zatrzymaj przy pierwszej uruchamiania wyjątku. W opisie zdarzenia wyjątków, ta flaga wskazuje, czy zdarzenie wyjątku jest zdarzeniem wyjątkach pierwszej szansy.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 Zatrzyma się w drugim uruchamiania wyjątku. W opisie zdarzenia wyjątków, oznacza zdarzenie wyjątku zdarzeń wyjątku drugiej szansy.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Zatrzymaj przy pierwszej uruchamiania wyjątku trybu użytkownika. W opisie zdarzenia wyjątków, oznacza zdarzenie wyjątku zdarzenie wyjątku pierwszej szansy użytkownika.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Przerwij po nieprzechwycony wyjątek trybu użytkownika. W opisie zdarzenia wyjątków, oznacza zdarzenie wyjątku zdarzenie wyjątku tryb nieprzechwyconego użytkownika.  
  
 EXCEPTION_STOP_ALL  
 Zatrzymaj na żadnym wyjątku. Nie można używać w opisie zdarzenia wyjątku.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 W opisie zdarzenia wyjątków, wskazuje, że wyjątek nie może być kontynuowane z.  
  
 EXCEPTION_CODE_SUPPORTED  
 Wskazuje, że wyjątek ma kod obsługujący go. Służącego do wyświetlania Wystąpił wyjątek  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Wskazuje, że kod wyjątku powinien być wyświetlany w formacie szesnastkowym. Używany podczas wyświetlania Wystąpił wyjątek.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Wskazuje, że kod wyjątku obsługuje JustMyCode. Używany podczas wyświetlania Wystąpił wyjątek.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Wskazuje, że debuger kodu zarządzanego obsługi wyjątków. Jeśli nie jest zestaw domyślny debuger obsługuje wyjątki. To jest przekazywana do [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) metody i nie są używane w [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktury.  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 PRZESTARZAŁE, NIE UŻYWAJ.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 PRZESTARZAŁE, NIE UŻYWAJ.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 PRZESTARZAŁE, NIE UŻYWAJ.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 PRZESTARZAŁE, NIE UŻYWAJ.  
  
## <a name="remarks"></a>Uwagi  
 Używane jako `dwState` członkiem [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktury do wskazywania stanu wyjątku i co można zrobić informacji na ten temat.  
  
 Te wartości są również przekazywane do [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) metodę, aby ustawić stan wszystkie wyjątki.  
  
 Te flagi mogą być łączone z bitowego OR.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)