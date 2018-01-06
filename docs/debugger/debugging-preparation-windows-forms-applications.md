---
title: 'Przygotowanie debugowania: Aplikacje biblioteki Windows form | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 01e9b9ced1db8f41c8ad1fb6386eec0d6080dd99
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-preparation-windows-forms-applications"></a>Przygotowanie debugowania: aplikacje Windows Forms
Szablon projektu formularzy systemu Windows umożliwia tworzenie aplikacji formularzy systemu Windows. Debugowanie tego typu aplikacji w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest prosta. Aby uzyskać więcej informacji, zobacz [Tworzenie nowego projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Podczas tworzenia projektu formularzy systemu Windows przy użyciu szablonu projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie tworzy wymagane ustawienia konfiguracji Debug i Release. W razie potrzeby możesz zmienić te ustawienia. Te ustawienia można zmienić w  **\<Nazwa projektu > strony właściwości** okno dialogowe (**mój projekt** w języku Visual Basic).  
  
 Aby uzyskać więcej informacji, zobacz [zalecane ustawienia właściwości](../debugger/managed-debugging-recommended-property-settings.md).  
  
 W poniższej tabeli przedstawiono jednego dodatkowe właściwości zalecane ustawienia.  
  
### <a name="configuration-properties-in-debug-tab"></a>Właściwości konfiguracji na karcie debugowania  
  
|**Nazwa właściwości**|**Ustawienie**|  
|-----------------------|-----------------|  
|**Uruchomienie akcji**|-Ustawioną **projektu Start** większość czasu. Ustaw **uruchomienia programu zewnętrznego** Jeśli chcesz uruchomić inny wykonywalny podczas uruchamiania debugowania (zazwyczaj na debugowanie bibliotek DLL).|  
  
 Można debugować aplikacji Windows Forms z wewnątrz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], lub przez podłączenie do już działającej aplikacji. Aby uzyskać więcej informacji dotyczących dołączania, zobacz [dołączyć do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Debugowanie aplikacji C#, F # lub Visual Basic program Windows Forms  
  
1.  Otwórz projekt w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Tworzenie punktów przerwania, zgodnie z potrzebami.  
  
     Ponieważ aplikacji formularzy systemu Windows są sterowane zdarzeniami, punkty przerwań przejdzie do kod obsługi zdarzenia lub do metody wywoływane przez kod obsługi zdarzenia. Do typowych zdarzeń, w którym można umieścić punkty przerwania obejmują:  
  
    1.  Zdarzenia związane z formantu, kliknij przycisk Enter, np.  
  
    2.  Zdarzenia związane z aplikacji uruchamiania i wyłączania, obciążenia, aktywny, np.  
  
    3.  Fokus i zdarzenia walidacji.  
  
     Aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach systemu Windows](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).  
  
3.  Na **debugowania** menu, kliknij przycisk **Start**.  
  
4.  Debugowanie za pomocą techniki opisane w [podstawy debugera](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [C#, F # i typy projektów Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Porady: Ustaw wartość Debug i Release konfiguracji](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Konfiguracje debugowania ustawienia projektu w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla języka Visual Basic konfiguracji debugowania](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](/dotnet/framework/winforms/index)