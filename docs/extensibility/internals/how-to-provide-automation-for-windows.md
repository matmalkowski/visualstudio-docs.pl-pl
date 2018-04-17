---
title: 'Porady: Podaj automatyzacji dla systemu Windows | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: c37123eeba42630b4b899966f7f4b0dc8c046fe8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-automation-for-windows"></a>Porady: Podaj automatyzacji dla systemu Windows
Możesz podać automatyzacji dla dokumentów i narzędzia systemu windows. Udostępnienie automatyzacji zalecane jest za każdym razem chcesz udostępnić obiekty automatyzacji w oknie i środowisko nie ma już obiekt automatyzacji gotowe, jak w przypadku listy zadań.

## <a name="automation-for-tool-windows"></a>Automatyzacja dla narzędzi systemu Windows
 Środowisko zawiera automatyzacji okna narzędzia zwracając standard <xref:EnvDTE.Window> obiekt opisane w poniższej procedurze:

#### <a name="to-provide-automation-for-tool-windows"></a>Aby zapewnić automatyzacji dla narzędzi systemu windows

1.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodę za pomocą środowiska z <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> jako `VSFPROPID` parametr, aby uzyskać `Window` obiektu.

2.  Gdy obiekt wywołujący żąda obiekt automatyzacji pakiet VSPackage specyficzne dla okna narzędzia za pośrednictwem <xref:EnvDTE.Window.Object%2A>, wywołania środowiska `QueryInterface` dla `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, lub `IDispatch` interfejsów. Zarówno `IExtensibleObject` i `IVsExtensibleObject` podaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> metody.

3.  Kiedy środowisko następnie wywołuje `GetAutomationObject` metody przekazywanie `NULL`, odpowiedź, przekazując kopii obiektu specyficzne dla pakiet VSPackage.

4.  Jeśli wywołanie `QueryInterface` dla `IExtensibleObject` i `IVsExtensibleObject` zakończy się niepowodzeniem, a następnie wywołuje środowiska `QueryInterface` dla `IDispatch`.

## <a name="automation-for-document-windows"></a>Automatyzacja dla okna dokumentów
 Standard <xref:EnvDTE.Document> obiektu jest również dostępny ze środowiska, chociaż Edytor może mieć własną implementację <xref:EnvDTE.Document> obiektu zaimplementowanie `IExtensibleObject` interfejsu i reagowanie na `GetAutomationObject`.

 Ponadto edytora może zapewnić pakiet VSPackage specyficzne dla obiekt automatyzacji, pobierane w drodze <xref:EnvDTE.Document.Object%2A> metody, implementując `IVsExtensibleObject` lub `IExtensibleObject` interfejsów. [Przykłady VSSDK](http://aka.ms/vs2015sdksamples) przyczynia się do obiektu automatyzacji specyficznych dla dokumentu RTF.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>