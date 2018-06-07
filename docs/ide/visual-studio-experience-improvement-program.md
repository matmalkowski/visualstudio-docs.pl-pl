---
title: Program poprawy jakości obsługi klienta
description: Dowiedz się, jak do zarządzania ustawieniami ochrony prywatności w programie Visual Studio.
ms.date: 05/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8dbc83a2d3fe1b2f5bb32a6baaf336c0a6c46e7d
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572637"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Program poprawy jakości obsługi klienta programu Visual Studio

Visual Studio klienta środowisko poprawy programu (VSCEIP) zaprojektowano w celu pomóc firmie Microsoft w ulepszaniu programu Visual Studio w czasie. Ten program [zbiera informacje o błędach](../ide/diagnostic-data-collection.md), komputera i jak osoby użyć programu Visual Studio, bez zakłócania pracy użytkowników w swoich zadań na komputerze. Informacje zbierane pomaga firma Microsoft może zidentyfikować funkcje wymagające poprawy. W tym dokumencie opisano sposób uczestnictwa w lub poza VSCEIP.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]

## <a name="opt-in-or-out"></a>OPT przychodzący lub wychodzący

VSCEIP jest domyślnie włączona. Można ją wyłączyć, lub z powrotem na, wykonując następujące instrukcje:

1. Uruchom program Visual Studio.

1. Z **pomocy** menu wskaż **Prześlij opinię**, a następnie wybierz **ustawienia**.

   **Program poprawy jakości obsługi programu Visual Studio** zostanie otwarte okno dialogowe.

1. Aby zrezygnować, wybierz **nie, nie chcę brać udziału**, a następnie wybierz **OK**.
   Aby włączyć, wybierz **tak, chcę uczestniczyć**, a następnie wybierz **OK**.

   ![Visual Program poprawy jakości obsługi Studio okna dialogowego](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Ustawienia rejestru

Jeśli zainstalujesz [Build Tools for Visual Studio](https://www.visualstudio.com/downloads/#build-tools-for-visual-studio-2017), należy zaktualizować rejestru w celu skonfigurowania VSCEIP. Klienci korporacyjni można konstruować zasady grupy do uczestnictwa w lub poza VSCEIP przez ustawienie zasad opartych na rejestrze.

Ustawienia i odpowiedni klucz rejestru są następujące:

W 64-bitowego systemu operacyjnego, klucz = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**  
W 32-bitowego systemu operacyjnego, klucz = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**  
Gdy zasady grupy są włączone, klucz = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**  

Wpis = **zgodzie**

Wartość = (DWORD)
- **0** jest wyłączony (Wyłącz VSCEIP)
- **1** zgłoszenie (Włącz VSCEIP)

> [!CAUTION]
> Niepoprawne edytowanie rejestru może spowodować poważne uszkodzenie systemu. Przed wprowadzeniem zmian w rejestrze należy wykonać kopię zapasową wszystkich cennych danych, które znajdują się na komputerze. Można również użyć **Ostatnia znana dobra konfiguracja** opcję uruchamiania w razie wystąpienia problemów po zastosowaniu zmiany ręcznie.

Aby uzyskać więcej informacji na temat informacji zbieranych, przetwarzanych lub przesyłanych przez VSCEIP, zobacz [zasady zachowania poufności informacji firmy Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Zobacz także

* [Informacje diagnostyczne zebrane przez program Visual Studio](diagnostic-data-collection.md)
* [Porozmawiaj z nami](../ide/talk-to-us.md)
* [Jak zgłosić problem z programem Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)
* [Społeczność deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/)
* [Zasady zachowania poufności informacji firmy Microsoft](https://privacy.microsoft.com/privacystatement)
