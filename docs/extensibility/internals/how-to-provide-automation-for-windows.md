---
title: 'Instrukcje: zapewnianie automatyzacji dla Windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9158ac7d133d30ae5fbca0281cbc55138e041f6
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510741"
---
# <a name="how-to-provide-automation-for-windows"></a>Instrukcje: zapewnianie automatyzacji dla systemu windows
Możesz podać automatyzacji dla dokumentu i narzędzi systemu windows. Udostępnienie usługi automation zalecane jest zawsze wtedy, gdy chcesz udostępnić obiektów automatyzacji w oknie, a środowisko nie zawiera już obiekt automatyzacji gotowych do użycia, jak w przypadku listy zadań.

## <a name="automation-for-tool-windows"></a>Automatyzacji dla okien narzędzi
 Środowisko zapewnia automatyzację w oknie narzędzi, zwracając standardowego <xref:EnvDTE.Window> obiektu zgodnie z opisem w poniższej procedurze:

### <a name="to-provide-automation-for-tool-windows"></a>Aby zapewnić automatyzacji dla okien narzędzi

1.  Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodę za pomocą środowiska z <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> jako `VSFPROPID` parametru, aby pobrać `Window` obiektu.

2.  Gdy obiekt wywołujący żąda obiekt automatyzacji specyficzne dla pakietu VSPackage dla okna narzędzia za pomocą <xref:EnvDTE.Window.Object%2A>, wywołania środowiska `QueryInterface` dla `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, lub `IDispatch` interfejsów. Zarówno `IExtensibleObject` i `IVsExtensibleObject` zapewniają <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> metody.

3.  Gdy środowisko następnie wywołuje `GetAutomationObject` metoda przekazywania `NULL`, Odpowiedz, przekazując kopii obiektu specyficzne dla pakietu VSPackage.

4.  Jeśli wywołanie `QueryInterface` dla `IExtensibleObject` i `IVsExtensibleObject` zakończy się niepowodzeniem, a następnie wywołuje środowisko `QueryInterface` dla `IDispatch`.

## <a name="automation-for-document-windows"></a>Automatyzacja okna dokumentu
 Standardowa <xref:EnvDTE.Document> obiektu jest również dostępna w środowisku, chociaż Edytor może mieć własną implementację <xref:EnvDTE.Document> obiekt poprzez implementację `IExtensibleObject` interfejsu i reagowanie na nie `GetAutomationObject`.

 Ponadto, edytor może zapewnić obiektu automatyzacji specyficzne dla pakietu VSPackage, pobierane w drodze <xref:EnvDTE.Document.Object%2A> metody, implementując `IVsExtensibleObject` lub `IExtensibleObject` interfejsów. [Przykłady VSSDK](http://aka.ms/vs2015sdksamples) przyczynia się do obiektu automatyzacji specyficzne dla dokumentu w formacie RTF.

## <a name="see-also"></a>Zobacz także
    
<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>