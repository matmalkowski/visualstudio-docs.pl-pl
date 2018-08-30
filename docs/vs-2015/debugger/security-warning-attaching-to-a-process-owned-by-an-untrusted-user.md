---
title: 'Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub niepewne, nie dołączaj do tego procesu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b856ac3a61d8af72d78546948bbe4ab780e9512e
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43231252"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub nie masz do nich pełnego zaufania, nie dołączaj do tego procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub niepewne, nie dołączaj do tego procesu](https://docs.microsoft.com/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process).  
  
To okno dialogowe ostrzeżenia pojawia się po dołączeniu do procesu, który zawiera kod częściowo zaufany lub właścicielem jest niezaufanego użytkownika natychmiast, zanim wystąpi dołączanie. Niezaufane procesu, który zawiera złośliwy kod ma potencjalnie uszkodzić komputer podczas debugowania. Jeśli masz powód, aby obdarzać procesu, a następnie kliknij przycisk **anulować** zapobiegające debugowania.  
  
 Aby pominąć to ostrzeżenie podczas debugowania uzasadnione scenariusz, zamknij program Visual Studio i ustawić wartość tego klucza rejestru 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, a następnie ponownie uruchom program Visual Studio. Po zakończeniu debugowania w scenariuszu, Zresetuj wartość 0, a następnie uruchom ponownie program Visual Studio.  
  
 "Zaufanych użytkowników" te obejmują samodzielnie oraz zestaw standardowych użytkowników, którzy są zazwyczaj definiowane na komputerach, które zostały zainstalowane, takie jak w programie .NET Framework `aspnet`, `localsystem`, `networkservice`, i `localservice`.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 Nazwa  
 Nazwa zestawu, wymagane do debugowania  
  
 Użytkownik  
 Bieżący użytkownik  
  
 Dołącz  
 Naciśnij klawisz, aby kontynuować debugowanie przez dołączenie  
  
 Nie dołączaj  
 Nie dołączaj do procesu  
  
## <a name="see-also"></a>Zobacz też  
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)



