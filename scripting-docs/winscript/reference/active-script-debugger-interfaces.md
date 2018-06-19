---
title: Interfejsy debugera aktywnego skryptu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger interfaces
- activdbg.h
ms.assetid: bf4750b1-4e58-442b-ab56-254e640de61d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4a3d17a8ff43bb3bd18641c2298f5436f40d925
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792349"
---
# <a name="active-script-debugger-interfaces"></a>Interfejsy debugera aktywnego skryptu
Pliki nagłówkowe activdbg.h i activdbg100.h zapewniają interfejsy, wyliczenia i struktury wymienione w tej sekcji. Są one do debugowania skryptów.  
  
> [!NOTE]
>  `IJSDebug*` Interfejsów i `IEnumJsStackFrames` interfejsu pierwszy zostały wydane w programie Internet Explorer 11 dla debugowanie kodu natywnego przy użyciu skryptu. Plik nagłówka do tych interfejsów jest jscript9diag.h.  
  
## <a name="in-this-section"></a>W tej sekcji  
 Następujące interfejsy Zezwalaj niezależny od języka, niezależny od hosta debugowania:  
  
-   [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
-   [Interfejs IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)  
  
-   [Interfejs IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)  
  
-   [Interfejs IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)  
  
-   [Interfejs IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)  
  
-   [Interfejs IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
  
-   [Interfejs IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)  
  
-   [Interfejs IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)  
  
-   [Interfejs IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)  
  
-   [Interfejs IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)  
  
-   [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
  
-   [Interfejs IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)  
  
-   [Interfejs IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)  
  
-   [Interfejs IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)  
  
-   [Interfejs IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
  
-   [Interfejs IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)  
  
-   [Interfejs IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)  
  
-   [Interfejs IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md)  
  
-   [Interfejs IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)  
  
-   [Interfejs IDebugAsyncOperationCallBack](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
  
-   [Interfejs IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)  
  
-   [Interfejs IDebugCookie](../../winscript/reference/idebugcookie-interface.md)  
  
-   [Interfejs IDebugDocument](../../winscript/reference/idebugdocument-interface.md)  
  
-   [Interfejs IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md)  
  
-   [Interfejs IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
  
-   [Interfejs IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)  
  
-   [Interfejs IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)  
  
-   [Interfejs IDebugDocumentProvider](../../winscript/reference/idebugdocumentprovider-interface.md)  
  
-   [Interfejs IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)  
  
-   [Interfejs IDebugDocumentTextAuthor](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
  
-   [Interfejs IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)  
  
-   [Interfejs IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)  
  
-   [Interfejs IDebugExpression](../../winscript/reference/idebugexpression-interface.md)  
  
-   [Interfejs IDebugExpressionCallBack](../../winscript/reference/idebugexpressioncallback-interface.md)  
  
-   [Interfejs IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)  
  
-   [Interfejs IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)  
  
-   [Interfejs IDebugHelper](../../winscript/reference/idebughelper-interface.md)  
  
-   [Interfejs IDebugSessionProvider](../../winscript/reference/idebugsessionprovider-interface.md)  
  
-   [Interfejs IDebugSessionProviderEx](../../winscript/reference/idebugsessionproviderex-interface.md)  
  
-   [Interfejs IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)  
  
-   [Interfejs IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)  
  
-   [Interfejs IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)  
  
-   [Interfejs IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)  
  
-   [Interfejs IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)  
  
-   [Interfejs IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  
-   [Interfejs IEnumDebugCodeContexts](../../winscript/reference/ienumdebugcodecontexts-interface.md)  
  
-   [Interfejs IEnumDebugExpressionContexts](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  
-   [Interfejs IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)  
  
-   [Ienumjsstackframes — interfejs](../../winscript/reference/ienumjsstackframes-interface.md)  
  
-   [Interfejs IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)  
  
-   [Interfejs IEnumRemoteDebugApplicationThreads](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  
-   [Ijsdebug — interfejs](../../winscript/reference/ijsdebug-interface.md)  
  
-   [Ijsdebugbreakpoint — interfejs](../../winscript/reference/ijsdebugbreakpoint-interface.md)  
  
-   [Ijsdebugdatatarget — interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)  
  
-   [Ijsdebugframe — interfejs](../../winscript/reference/ijsdebugframe-interface.md)  
  
-   [Ijsdebugprocess — interfejs](../../winscript/reference/ijsdebugprocess-interface.md)  
  
-   [Ijsdebugproperty — interfejs](../../winscript/reference/ijsdebugproperty-interface.md)  
  
-   [Ijsdebugstackwalker — interfejs](../../winscript/reference/ijsdebugstackwalker-interface.md)  
  
-   [Ijsenumdebugproperty — interfejs](../../winscript/reference/ijsenumdebugproperty-interface.md)  
  
-   [Interfejs IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)  
  
-   [Interfejs IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
  
-   [Interfejs IMachineDebugManagerEvents](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
  
-   [Interfejs IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)  
  
-   [Interfejs IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)  
  
-   [Interfejs IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)  
  
-   [Interfejs IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)  
  
-   [Interfejs IRemoteDebugApplicationEx](../../winscript/reference/iremotedebugapplicationex-interface.md)  
  
-   [Interfejs IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
  
-   [Interfejs IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)  
  
-   [Interfejs IRemoteDebugApplicationThreadEx](../../winscript/reference/iremotedebugapplicationthreadex-interface.md)  
  
-   [Interfejs ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)  
  
-   [Interfejs ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)  
  
-   [Interfejs IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md)  
  
-   [Interfejs IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)  
  
 W poniższej sekcji przedstawiono stałe, wyliczenia i struktury używane do debugowania:  
  
-   [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd debugowania aktywnego skryptu](../../winscript/active-script-debugging-overview.md)