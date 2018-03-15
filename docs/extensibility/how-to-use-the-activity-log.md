---
title: "Porady: Korzystanie z dziennika aktywności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9f45e18ebb2ab3e83041ea0e1ba5c2de4c9b8532
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="how-to-use-the-activity-log"></a>Porady: Korzystanie z dziennika aktywności
VSPackages może zapisywać komunikaty dziennika aktywności. Ta funkcja jest szczególnie przydatna w przypadku debugowania VSPackages w środowiskach sprzedaży detalicznej.  
  
> [!TIP]
>  Dziennik aktywności jest zawsze włączone. Visual Studio zachowuje stopniowego bufor pozycji ostatnio 100, a także 10 pierwszych wpisów, których konfiguracji ogólnych informacji.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Aby zapisać wpis w dzienniku aktywności  
  
1.  Wstaw ten kod w <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody lub w innej metody, z wyjątkiem konstruktora pakiet VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Ten kod pobiera <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> usługi i rzutuje do <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejsu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> zapisuje informacyjną wejścia przy użyciu bieżącej kultury kontekstu dziennika aktywności.  
  
2.  Po załadowaniu pakiet VSPackage (zazwyczaj po wywołaniu polecenia lub otwarciu okna) tekst jest zapisywane w dzienniku aktywności.  
  
### <a name="to-examine-the-activity-log"></a>Aby sprawdzić dziennik aktywności  
  
1.  Uruchom program Visual Studio z [/Log](../ide/reference/log-devenv-exe.md) przełącznik wiersza polecenia do zapisania ActivityLog.xml dysku podczas sesji.

2.  Po zamknięciu programu Visual Studio, znajdowanie dziennika aktywności w podfolderze dla danych programu Visual Studio: *% AppData %*\Microsoft\VisualStudio\15.0\ActivityLog.xml.  
  
3.  Otwórz dziennik aktywności w dowolnym edytorze tekstu. Poniżej przedstawiono typowe wpis:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Ponieważ usługa jest dziennik aktywności, dziennika aktywności jest niedostępny w Konstruktorze pakiet VSPackage.  
  
 Dziennik aktywności powinna uzyskać bezpośrednio przed zapisywania do niego. Nie buforuj lub dziennik aktywności do użytku w przyszłości.  
  
## <a name="see-also"></a>Zobacz też
 [/ Log (devenv.exe)](../ide/reference/log-devenv-exe.md)   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Rozwiązywanie problemów z VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)
