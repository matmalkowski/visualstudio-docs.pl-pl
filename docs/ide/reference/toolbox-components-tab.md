---
title: "Przybornik, karta składniki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bb474e832f815453fd84ba35bc3680b961e17954
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="toolbox-components-tab"></a>Przybornik, karta Składniki
Wyświetla składniki, które można dodać do [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektantów. Oprócz [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] składników, które są dołączone do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], takich jak <xref:System.Messaging.MessageQueue> i <xref:System.Diagnostics.EventLog> składników, można dodać użytkownika składników własnych lub innej firmy do tej karty. Aby uzyskać więcej informacji, zobacz [porady: manipulowanie karty przybornika](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 Aby wyświetlić tę kartę z **widoku** menu, wybierz opcję **przybornika**. W **przybornika**, wybierz pozycję **składniki** kartę.  
  
 **Proces BackgroundWorker**  
 Tworzy `System.ComponentModel.BackgroundWorker` wystąpienie składnika, które można uruchomić operacji w oddzielnych, dedykowane wątku.  
  
 **DirectoryEntry**  
 Tworzy <xref:System.DirectoryServices.DirectoryEntry> wystąpienie składnika, który hermetyzuje węzeł lub obiekt w hierarchii usługi Active Directory i może służyć do interakcji z dostawców usługi Active Directory.  
  
 **DirectorySearcher**  
 Tworzy <xref:System.DirectoryServices.DirectorySearcher> wystąpienie składnika, których można użyć do wykonania zapytania względem usługi Active Directory.  
  
 **ErrorProvider**  
 Tworzy `System.Windows.Forms.ErrorProvider` wystąpienie składnika, co oznacza użytkownika końcowego, że kontrolkę w formularzu ma skojarzone z nim błąd.  
  
 **Dziennik zdarzeń**  
 Tworzy <xref:System.Diagnostics.EventLog> wystąpienie składnika służy do interakcji z systemem i niestandardowe dzienniki zdarzeń, w tym zapisu do dziennika zdarzeń i odczytywanie danych dziennika. Aby uzyskać więcej informacji, zobacz [wprowadzenie do składnika EventLog](http://msdn.microsoft.com/en-us/a2ba4f28-4b1a-435e-99ef-51b28e21f805).  
  
 **Element FileSystemWatcher**  
 Tworzy <xref:System.IO.FileSystemWatcher> wystąpienie składnika, który służy do monitorowania zmian do dowolnego katalogu lub pliku, do których masz dostęp. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie wystąpień składnika FileSystemWatcher](http://msdn.microsoft.com/en-us/2e628234-4951-4135-8a86-28b924070d50).  
  
 **Helpprovider —**  
 Tworzy `System.Windows.Forms.HelpProvider` wystąpienie składnika, który zawiera menu podręczne lub pomoc dla formantów.  
  
 **Listy obrazów**  
 Tworzy `System.Windows.Forms.ImageList` wystąpienie składnika, który udostępnia metody umożliwiające zarządzanie kolekcją `System.Drawing.Image` obiektów.  
  
 **MessageQueue**  
 Tworzy <xref:System.Messaging.MessageQueue> wystąpienie składnika, który służy do interakcji z kolejek wiadomości, w tym odczytywania wiadomości z oraz zapisywanie wiadomości do kolejki, przetwarzania transakcji i wykonywania zadań administracyjnych kolejki. Aby uzyskać więcej informacji, zobacz [przy użyciu składników obsługi wiadomości](http://msdn.microsoft.com/en-us/922dbac7-26f0-4e39-b666-ccfc184793d7).  
  
 **PerformanceCounter**  
 Tworzy <xref:System.Diagnostics.PerformanceCounter> wystąpienie składnika, które służy do interakcji z liczników wydajności systemu Windows, w tym tworzenie nowych kategorii i wystąpień, odczytywanie wartości z liczników i wykonywania obliczeń w danych licznika. Aby uzyskać więcej informacji, zobacz [progi monitorowania wydajności](http://msdn.microsoft.com/en-us/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).  
  
 **Proces**  
 Tworzy <xref:System.Diagnostics.Process> wystąpienie składnika można zatrzymać, uruchomić i manipulowania danymi powiązanymi z procesów w systemie. Aby uzyskać więcej informacji, zobacz [monitorowanie i zarządzanie procesów systemu Windows](http://msdn.microsoft.com/en-us/a86bd4c1-b92c-49a0-8f32-61d67837b45e).  
  
 **Klasy SerialPort**  
 Tworzy `System.IO.Ports.SerialPort` wystąpienie składnika, które oferuje synchroniczne i sterowane zdarzeniami we/wy, dostępu do numeru pin i podział stanów i dostęp do właściwości sterownik szeregowy.  
  
 **ServiceController**  
 Tworzy <xref:System.ServiceProcess.ServiceController> wystąpienie składnika służy do modyfikowania istniejących usług, w tym uruchamianie i zatrzymywanie usług oraz wysyłanie poleceń do nich. Aby uzyskać więcej informacji, zobacz [monitorowania usług systemu Windows](http://msdn.microsoft.com/en-us/4542ee3f-e052-4cb9-8726-58e9420de222).  
  
 **Czasomierz**  
 Tworzy <xref:System.Windows.Forms.Timer> wystąpienie składnika można użyć, aby dodać funkcje oparte na czasie do aplikacji opartych na systemie Windows. Aby uzyskać więcej informacji, zobacz [Timer — składnik](/dotnet/framework/winforms/controls/timer-component-windows-forms).  
  
> [!NOTE]
>  Istnieje również na podstawie systemu <xref:System.Timers.Timer> dodawanego do **przybornika** to <xref:System.Timers.Timer> jest zoptymalizowana pod kątem aplikacji serwerowych i formularze systemu Windows <xref:System.Windows.Forms.Timer> najlepiej nadaje się do użycia w formularzach systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie przy użyciu składników](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)   
 [Wskazówki dotyczące programowania w języku składnika](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)   
 [Przybornika](../../ide/reference/toolbox.md)   
 [Wybierz elementy przybornika, okno dialogowe (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)