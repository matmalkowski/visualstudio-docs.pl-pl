---
title: Interfejs IDebugApplication | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07964292785634212099a0bfcf8174ebb55e8713
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication-interface"></a>Interfejs IDebugApplication
Opisuje metody debugowania-remote, do użytku przez aparaty języka i hostów.  
  
 Oprócz dziedziczone z metody `IRemoteDebugApplication`, `IDebugApplication` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Ustawia nazwę aplikacji.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Powiadamia menedżera debugowania procesu aparat języka, w trybie pojedynczy krok o zbliżającym się zwrócić do swojego obiektu wywołującego.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Powoduje, że dany ciąg znaków, który będzie wyświetlany przez debuger IDE.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Uruchamia domyślny debuger IDE i dołącza sesji debugowania do tej aplikacji, jeśli nie jest już dołączony.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Powoduje, że bieżący wątek zablokować, a następnie wysyła powiadomienie z informacją o punkt przerwania do debugera w IDE.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Powoduje, że tej aplikacji zwolnić wszystkie odwołania, a następnie wprowadź nieaktywny.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Zwraca bieżące flagi podziału dla aplikacji.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Zwraca wątek skojarzony z aktualnie uruchomiony.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Udostępnia asynchroniczne operacji danego synchroniczne debugowania.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Dodaje dostawcę modułu wyliczającego ramki stosu w tej aplikacji.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Usuwa dostawcę modułu wyliczającego ramki stosu z tej aplikacji.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Określa, czy bieżący wątek uruchomiony wątek debugera.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Udostępnia mechanizm dla obiekt wywołujący, aby uruchomić kod w wątku debugera.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Tworzy nowy węzeł aplikacji skojarzonej z dostawcy określonego dokumentu.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Wyzwala zdarzenie generyczne debugera `IApplicationDebugger` interfejsu.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Powoduje, że bieżący wątek zablokować, a następnie wysyła powiadomienie z informacją o błędzie do debugera w IDE.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Określa, czy jest zarejestrowany debuger just in time (JIT).|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Określa, czy debugera JIT jest zarejestrowana dla hostów bez automatycznego debugowania.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Dodaje dostawcę kontekstu wyrażenia globalnego do tej aplikacji.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Usuwa dostawca kontekstu wyrażenia globalnego z tej aplikacji.|