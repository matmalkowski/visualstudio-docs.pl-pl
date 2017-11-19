---
title: "Porady: Korzystanie z dziennika aktywności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d08cd747c762d7820e4744251fb00abff22b3fdc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-the-activity-log"></a>Porady: Korzystanie z dziennika aktywności
VSPackages może zapisywać komunikaty dziennika aktywności. Ta funkcja jest szczególnie przydatna w przypadku debugowania VSPackages w środowiskach sprzedaży detalicznej.  
  
> [!TIP]
>  Dziennik aktywności jest zawsze włączone. Visual Studio zachowuje stopniowego buforu wpisy ostatnio sto, a także pierwszych dziesięciu wpisów, których konfiguracji ogólnych informacji.  
  
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
  
     Ten kod pobiera <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> usługi i rzutuje do <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejsu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>zapisuje informacyjną wejścia przy użyciu bieżącej kultury kontekstu dziennika aktywności.  
  
2.  Po załadowaniu pakiet VSPackage (zazwyczaj po wywołaniu polecenia lub otwarciu okna) tekst jest zapisywane w dzienniku aktywności.  
  
### <a name="to-examine-the-activity-log"></a>Aby sprawdzić dziennik aktywności  
  
1.  Znajdowanie dziennika aktywności w podfolderze dla danych programu Visual Studio: *% AppData %*\Microsoft\VisualStudio\15.0\ActivityLog.XML...  
  
2.  Otwórz dziennik aktywności w dowolnym edytorze tekstu. Poniżej przedstawiono typowe wpis:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Ponieważ usługa jest dziennik aktywności, dziennika aktywności jest niedostępny w Konstruktorze pakiet VSPackage.  
  
 Dziennik aktywności powinna uzyskać bezpośrednio przed zapisywania do niego. Nie buforuj lub dziennik aktywności do użytku w przyszłości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Rozwiązywanie problemów z VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
