---
title: Strona debugowania, Projektant projektu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 305f5160ab91fdfa61e9133ab9f867194e4a117f
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="debug-page-project-designer"></a>Strona debugowania, Projektant projektu
> [!WARNING]
>  Ten temat nie dotyczy aplikacji platformy uniwersalnej systemu Windows. Zobacz [rozpocząć sesję debugowania: (VB, C#, C++ i XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) w Centrum deweloperów systemu Windows.  
  
 Użyj **debugowania** strony **projektanta projektu** można ustawić właściwości dla debugowania zachowanie w projektach Visual Basic lub C#.  
  
 Aby uzyskać dostęp do **debugowania** wybierz węzeł projektu w **Eksploratora rozwiązań**. Na **projektu** menu, wybierz * ProjectName ***właściwości**. Gdy **Projektant projektu** zostanie wyświetlony, kliknij przycisk **debugowania** kartę.  
  
## <a name="configuration-and-platform"></a>Konfiguracja i platforma  
 Poniższe opcje pozwalają na wybierz configuration i platform, aby wyświetlić lub zmodyfikować.  
  
 **Konfiguracja**  
 Określa, które ustawienia konfiguracji, aby wyświetlić lub zmodyfikować. Te ustawienia mogą być **debugowania** (ustawienie domyślne), **wersji**, lub **wszystkie konfiguracje**.
  
 **Platformy**  
 Określa, które ustawienia platformy, aby wyświetlić lub zmodyfikować. Można wybierać **Any CPU** (ustawienie domyślne), **x64**, i **x86**.
  
## <a name="start-action"></a>Uruchomienie akcji  
 **Uruchomienie akcji** wskazuje element, aby uruchomić podczas debugowania aplikacji: projekt, program niestandardowy, adres URL lub nothing. Domyślnie ta opcja jest ustawiona na **rozpoczęcia projektu**. **Akcja uruchamiania** ustawienie **debugowania** strony określa wartość `StartAction` właściwości.  
  
 **Uruchom projekt**  
 Wybierz tę opcję, aby określić, że plik wykonywalny (w przypadku projektów aplikacji systemu Windows i aplikacji konsoli) powinna być uruchamiana podczas debugowania aplikacji. Ta opcja jest domyślnie wybrana.  
  
 **Uruchom program zewnętrznych**  
 Wybierz tę opcję, aby określić, że określony program można uruchomić podczas debugowania aplikacji.  
  
 **Uruchom przeglądarkę z adresem URL**  
 Wybierz tę opcję, aby określić, czy adres URL jest dostępna podczas debugowania aplikacji.  
  
## <a name="start-options"></a>Opcje uruchamiania  
 **Argumenty wiersza polecenia**  
 W tym polu tekstowym wprowadź argumenty wiersza polecenia używane do debugowania.  
  
 **Katalog roboczy**  
 W tym polu tekstowym wprowadź katalogu, z którego będzie uruchamiana projektu. Lub kliknij przycisk Przeglądaj (**...** ) można wybrać katalog.  
  
 **Użyj komputera zdalnego**  
 Aby debugować aplikację z komputera zdalnego, zaznacz to pole wyboru, a następnie wprowadź ścieżkę do komputera zdalnego, w polu tekstowym.  
  
## <a name="enable-debuggers"></a>Włącz debugery  
 **Włącz debugowanie kodu niezarządzanego**  
 Ta opcja określa, czy obsługiwane jest debugowanie kodu natywnego. Zaznacz to pole wyboru, jeśli wywołania do obiektów COM lub uruchomić program niestandardowy zapisywane w kodzie natywnym, który odwołuje się do projektu i musi debugowanie kodu natywnego. Wyczyść to pole wyboru, aby wyłączyć debugowanie kodu niezarządzanego. To pole wyboru jest domyślnie wyczyszczone.  
  
 **Włącz debugowanie serwera SQL**  
 Wybierz lub wyczyść to pole wyboru, aby włączyć lub wyłączyć debugowanie SQL procedur z aplikacji Visual Basic. To pole wyboru jest domyślnie wyczyszczone.  
  
 **Włącz procesu hostingu Visual Studio**  
 Zaznacz to pole wyboru, aby włączyć procesu hostingu Visual Studio. To pole wyboru jest zaznaczone domyślnie. Aby uzyskać więcej informacji, zobacz [proces hostingu (vshost.exe)](../../ide/hosting-process-vshost-exe.md).  
  
 Aby debugować w strefie zabezpieczeń, należy włączyć tę opcję i **Debuguj aplikację z wybranym zestawem uprawnień** w [okno dialogowe Zaawansowane ustawienia zabezpieczeń](../../ide/reference/advanced-security-settings-dialog-box.md).  
  
## <a name="see-also"></a>Zobacz także

[Debugowanie w programie Visual Studio](../../debugger/debugging-in-visual-studio.md)  
[Konfiguracje debugowania ustawienia projektu w języku C#](../../debugger/project-settings-for-csharp-debug-configurations.md)  
[Ustawienia projektu dla języka Visual Basic konfiguracji debugowania](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)  
[Instrukcje: debugowanie aplikacji ClickOnce przy użyciu ograniczonych uprawnień](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)  
[Instrukcje: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md)