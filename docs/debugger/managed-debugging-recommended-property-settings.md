---
title: 'Debugowanie zarządzane: Zalecane ustawienia właściwości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e51a57f1929f4ba63bb4117e6dc496b52f2c20a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="managed-debugging-recommended-property-settings"></a>Zarządzanie debugowaniem: zalecane ustawienia właściwości
Taki sam sposób, w przypadku wszystkich scenariuszy debugowania zarządzanego można ustawić niektórych właściwości.  
  
 Poniższe tabele Wyświetl zalecane ustawienia właściwości.  
  
 Ustawienia niewymienione w tym może się różnić między typów różnych projektów zarządzanych. Na przykład **Akcja uruchamiania** zostaną ustawione inaczej w projekcie formularzy systemu Windows, niż w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projektu.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Właściwości konfiguracji na kompilacji (C#) lub na karcie kompilacji (Visual Basic)  
  
|**Nazwa właściwości**|**Ustawienie**|  
|-----------------------|-----------------|  
|**Zdefiniuj stała debugowania**|C# i F #: Ustaw pole wyboru zaznaczenia. Umożliwia to aplikacji umożliwiająca użycie klasy debugowania.|  
|**Zdefiniuj stała śledzenia**|C# i F #: Ustaw pole wyboru zaznaczenia. Dzięki temu aplikacja korzysta z klasy śledzenia.|  
|**Optymalizacja kodu**|C#, F # i Visual Basic: wartość false. Kod zoptymalizowany jest trudniej debugowania, ponieważ nie odpowiadają wygenerowanego instrukcje bezpośrednio w kodzie źródłowym. Jeśli program zawiera usterkę, która jest wyświetlana tylko w zoptymalizowanym kodzie, możesz włączyć to ustawienie, ale należy pamiętać, że kodem przedstawionym w **dezasemblacji** okna jest generowany na podstawie zoptymalizowane źródła, które mogą być niezgodne zobacz w kodzie Edytor. Aby debugowania zoptymalizowanego kodu, należy wyłączyć opcję tylko mój kod. (Zobacz [Ogranicz wykonywanie krok po kroku, aby tylko mój kod](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Aby uzyskać więcej informacji, zobacz [ustawienia projektu C# debugowania konfiguracji](../debugger/project-settings-for-csharp-debug-configurations.md) lub [ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Ścieżka danych wyjściowych**|Ustaw bin\Debug\\.|  
|**Opcje zaawansowane kompilacji**|Tylko języka Visual Basic. Kliknij przycisk **zaawansowane** Aby ustawić zaawansowane właściwości, które zostały opisane w poniższej tabeli.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>Zaawansowane ustawienia kompilatora — Okno dialogowe  
  
|**Nazwa właściwości**|**Ustawienie**|  
|-----------------------|-----------------|  
|**Włącz optymalizacje**|Wartość false dla przyczyn wymienionych w **Optymalizuj kod** opcji w powyższej tabeli.|  
|**Generuj informacje debugowania**|Zaznacz to pole wyboru powoduje flagi/Debug, należy ustawić podczas kompilowania, co spowoduje informacje potrzebne do ułatwienia debugowania.|  
|**Zdefiniuj stała debugowania**|Zaznacz to pole wyboru, aby zdefiniować `DEBUG` stałą, która pozwala aplikacji używać <xref:System.Diagnostics.Debug> klasy.|  
|**Zdefiniuj stała śledzenia**|Zaznacz to pole wyboru, aby zdefiniować `TRACE` stałą, która pozwala aplikacji używać <xref:System.Diagnostics.Trace> klasy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [C#, F # i typy projektów Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)