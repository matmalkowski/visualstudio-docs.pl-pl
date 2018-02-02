---
title: "Przybornik, karta składniki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: aa91db706d7e1236162ef69e6fd31e791ed44dbb
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="toolbox-components-tab"></a>Przybornik, karta Składniki

Wyświetla składniki, które można dodać do projektantów języka Visual Basic i C#. Oprócz składników .NET Framework, które są dołączone do programu Visual Studio, takich jak <xref:System.Messaging.MessageQueue> i <xref:System.Diagnostics.EventLog> składników, można dodać użytkownika składników własnych lub innej firmy do tej karty.
  
 Aby wyświetlić tę kartę z **widoku** menu, wybierz opcję **przybornika**. W **przybornika**, wybierz pozycję **składniki** kartę.  
  
 **BackgroundWorker**  
 Tworzy `System.ComponentModel.BackgroundWorker` wystąpienie składnika, które można uruchomić operacji w oddzielnych, dedykowane wątku.  
  
 **DirectoryEntry**  
 Tworzy <xref:System.DirectoryServices.DirectoryEntry> wystąpienie składnika, który hermetyzuje węzeł lub obiekt w hierarchii usługi Active Directory i może służyć do interakcji z dostawców usługi Active Directory.  
  
 **DirectorySearcher**  
 Tworzy <xref:System.DirectoryServices.DirectorySearcher> wystąpienie składnika, których można użyć do wykonania zapytania względem usługi Active Directory.  
  
 **ErrorProvider**  
 Tworzy `System.Windows.Forms.ErrorProvider` wystąpienie składnika, co oznacza użytkownika końcowego, że kontrolkę w formularzu ma skojarzone z nim błąd.  
  
 **EventLog**  
 Tworzy <xref:System.Diagnostics.EventLog> wystąpienie składnika służy do interakcji z systemem i niestandardowe dzienniki zdarzeń, w tym zapisu do dziennika zdarzeń i odczytywanie danych dziennika.
  
 **FileSystemWatcher**  
 Tworzy <xref:System.IO.FileSystemWatcher> wystąpienie składnika, który służy do monitorowania zmian do dowolnego katalogu lub pliku, do których masz dostęp.
  
 **Helpprovider —**  
 Tworzy `System.Windows.Forms.HelpProvider` wystąpienie składnika, który zawiera menu podręczne lub pomoc dla formantów.  
  
 **ImageList**  
 Tworzy `System.Windows.Forms.ImageList` wystąpienie składnika, który udostępnia metody umożliwiające zarządzanie kolekcją `System.Drawing.Image` obiektów.  
  
 **MessageQueue**  
 Tworzy <xref:System.Messaging.MessageQueue> wystąpienie składnika, który służy do interakcji z kolejek wiadomości, w tym odczytywania wiadomości z oraz zapisywanie wiadomości do kolejki, przetwarzania transakcji i wykonywania zadań administracyjnych kolejki.

 **PerformanceCounter**  
 Tworzy <xref:System.Diagnostics.PerformanceCounter> wystąpienie składnika, które służy do interakcji z liczników wydajności systemu Windows, w tym tworzenie nowych kategorii i wystąpień, odczytywanie wartości z liczników i wykonywania obliczeń w danych licznika.
  
 **Proces**  
 Tworzy <xref:System.Diagnostics.Process> wystąpienie składnika można zatrzymać, uruchomić i manipulowania danymi powiązanymi z procesów w systemie.
  
 **SerialPort**  
 Tworzy `System.IO.Ports.SerialPort` wystąpienie składnika, które oferuje synchroniczne i sterowane zdarzeniami we/wy, dostępu do numeru pin i podział stanów i dostęp do właściwości sterownik szeregowy.  
  
 **ServiceController**  
 Tworzy <xref:System.ServiceProcess.ServiceController> wystąpienie składnika służy do modyfikowania istniejących usług, w tym uruchamianie i zatrzymywanie usług oraz wysyłanie poleceń do nich.
  
 **Timer**  
 Tworzy <xref:System.Windows.Forms.Timer> wystąpienie składnika można użyć, aby dodać funkcje oparte na czasie do aplikacji opartych na systemie Windows. Aby uzyskać więcej informacji, zobacz [Timer — składnik](/dotnet/framework/winforms/controls/timer-component-windows-forms).  
  
> [!NOTE]
>  Istnieje również na podstawie systemu <xref:System.Timers.Timer> dodawanego do **przybornika** to <xref:System.Timers.Timer> jest zoptymalizowana pod kątem aplikacji serwerowych i formularze systemu Windows <xref:System.Windows.Forms.Timer> najlepiej nadaje się do użycia w formularzach systemu Windows.  
  
## <a name="see-also"></a>Zobacz także

[Programowanie przy użyciu składników](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
[Wskazówki dotyczące programowania w języku składnika](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)  
[Przybornik](../../ide/reference/toolbox.md)