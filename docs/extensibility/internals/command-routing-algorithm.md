---
title: Polecenie algorytmu routingu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aba7ddcdda4dd4eabbb9266e0fa89c916bb028f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131501"
---
# <a name="command-routing-algorithm"></a>Polecenie algorytmu routingu
W programie Visual Studio polecenia są obsługiwane przez wiele różnych składników. Polecenia są kierowane z najbardziej kontekstu, która jest oparta na bieżącym zaznaczeniu, peryferyjnych kontekst (znanej także jako globalny). Aby uzyskać więcej informacji, zobacz [dostępności](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Kolejność rozpoznawania polecenia  
 Polecenia są przekazywane za pośrednictwem następujących poziomów kontekst polecenia:  
  
1.  Dodatki: Środowisko oferuje najpierw polecenie dodatków znajdujących się.  
  
2.  Priorytet polecenia: te polecenia są rejestrowane za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Są wywoływane dla każdego polecenia w programie Visual Studio i są wywoływane w kolejności, w którym zostały zarejestrowane.  
  
3.  Polecenia w menu kontekstowym: polecenie znajduje się w menu kontekstowym najpierw jest oferowany na elemencie docelowym polecenia, który został dostarczony do menu kontekstowego, a następnie do typowych routingu.  
  
4.  Obiekty docelowe poleceń ustaw narzędzi: te obiekty docelowe poleceń są rejestrowane, gdy zgłaszasz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. `pCmdTarget` Parametr może być `null`. Jeśli nie jest `null`, a następnie używane do aktualizowania żadnych poleceń znajdujących się na pasku narzędzi konfigurujesz ten element docelowy polecenia. Jeśli powłoki konfiguruje paska narzędzi, a następnie przekazuje ją jako ramki okna `pCmdTarget` tak, aby wszystkie aktualizacje poleceń na przepływ z paska narzędzi przez ramki okna, nawet jeśli nie jest aktywny.  
  
5.  Okno narzędzi: Narzędzia systemu windows, które implementują zwykle <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejsu, powinny również implementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu, dzięki czemu Visual Studio można pobrać element docelowy polecenia, gdy okno jest aktywne okno. Jeśli jednak okna narzędzia, która ma fokus jest **projektu** okna, a następnie polecenie jest kierowany do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejs, który jest Wspólnemu elementowi nadrzędnemu wybranych elementów. Jeśli to pole wyboru, które obejmuje wiele projektów, polecenie jest kierowany do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> hierarchii. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Interfejs zawiera <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metody, które są podobne do odpowiednich poleceń na <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu.  
  
6.  Okno dokumentu: Jeśli polecenie ma flagę RouteToDocs w pliku vsct, Visual Studio szuka elementu docelowego polecenia dla obiektu widoku dokumentu, który może być wystąpienia <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejsu lub wystąpienia obiektu dokumentu (zazwyczaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>interfejsu lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfejs). Jeśli obiekt widoku dokumentu nie obsługuje polecenia, programu Visual Studio kieruje polecenie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs, który jest zwracany. (Jest to opcjonalny interfejs dla obiektów danych dokumentu).  
  
7.  Bieżącej hierarchii: bieżącej hierarchii może być projektu, który jest właścicielem aktywne okno dokumentu lub wybranej w hierarchii **Eksploratora rozwiązań**. Program Visual Studio jest szuka <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu implementowanego w hierarchii bieżącej lub aktywny. Hierarchia powinien obsługiwać poleceń, które są prawidłowe, gdy hierarchia jest aktywne, nawet wtedy, gdy okno dokumentu elementu projektu ma fokus. Jednak polecenia, które są stosowane tylko wtedy, gdy **Eksploratora rozwiązań** ma fokus musi być obsługiwany przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejsu i jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>metody.  
  
     **Wytnij**, **kopiowania**, **Wklej**, **usunąć**, **zmienić**, **wprowadź**i **DoubleClick** poleceń, które wymagają specjalnej obsługi. Aby uzyskać informacje o sposobie obsługi **usunąć** i **Usuń** poleceń w hierarchii, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interfejsu.  
  
8.  Globalny: Jeśli polecenie nie zostało obsłużone przez wymienione wcześniej kontekstów, Visual Studio próbuje kierowania go do pakiet VSPackage, który jest właścicielem polecenia, który implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Jeśli nie został już załadowany pakiet VSPackage, nie jest ona załadowana podczas wywołania programu Visual Studio <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. Pakiet VSPackage został załadowany tylko wtedy, gdy <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metoda jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie poleceń](../../extensibility/internals/command-design.md)