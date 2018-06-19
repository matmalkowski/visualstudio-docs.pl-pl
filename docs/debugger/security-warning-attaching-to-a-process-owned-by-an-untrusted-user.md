---
title: 'Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należących do niezaufanych użytkownika może być niebezpieczne. Jeśli nie wiesz, poniższe informacje wyglądają podejrzanie, nie dołączaj do tego procesu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68d88e01dde07789467272db830cae45ca5d60c4
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34178011"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należących do niezaufanych użytkownika może być niebezpieczne. Jeśli nie wiesz, poniższe informacje wyglądają podejrzanie, nie dołączaj do tego procesu
To okno dialogowe Ostrzeżenie pojawia się podczas dołączania do procesu, który zawiera kod częściowo zaufany lub jest własnością niezaufany użytkownik natychmiast, zanim nastąpi jego Podłączanie. Proces niezaufanych, zawierającego złośliwy kod ma potencjalnie uszkodzić komputer podczas debugowania. Jeśli masz powód, aby obdarzać procesu, a następnie kliknij przycisk **anulować** aby uniemożliwić debugowaniu.  
  
 Aby pominąć to ostrzeżenie podczas debugowania uzasadnionych scenariusz, zamknij program Visual Studio i ustawić wartość tego klucza rejestru 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, a następnie uruchom ponownie program Visual Studio. Po zakończeniu debugowania tego scenariusza, Zresetuj wartość 0, a następnie ponownie program Visual Studio.  
  
 "Zaufanych użytkowników" obejmują użytkownika, a także zestaw standardowych użytkowników, którzy są zazwyczaj definiowane na komputerach, które zostały zainstalowane, takich jak w programie .NET Framework `aspnet`, `localsystem`, `networkservice`, i `localservice`.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 Nazwa  
 Nazwa zestawu wymagane do debugowania  
  
 Użytkownik  
 Bieżący użytkownik  
  
 Dołącz  
 Naciśnij, aby kontynuować debugowanie dołączając  
  
 Dołączanie nie  
 Nie dołączaj do procesu  
  
## <a name="see-also"></a>Zobacz też  
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)