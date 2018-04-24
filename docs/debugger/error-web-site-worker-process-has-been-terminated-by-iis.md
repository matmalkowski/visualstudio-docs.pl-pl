---
title: 'Błąd: proces roboczy witryny sieci Web został zakończony przez Internetowe usługi informacyjne | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca76a0e66073d0102adb97d8cc4ca35087399297
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Błąd: proces roboczy witryny sieci Web został zakończony przez usługę IIS
Debuger zatrzymana wykonywanie kodu w witrynie sieci Web. Przyczyną Internet Information Services (IIS) do wniosku, że proces roboczy ma przestał odpowiadać. W związku z tym IIS przedwcześnie zakończył proces roboczy.  
  
 Aby przejść do debugowania, należy skonfigurować usług IIS, aby umożliwić proces roboczy kontynuować. Ten komunikat o błędzie nie jest widoczna z wersjami usług IIS, które są starsze niż IIS 7.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Aby skonfigurować usługi IIS 7 umożliwiają proces roboczy kontynuować  
  
1.  Otwórz **narzędzia administracyjne** okna.  
  
    1.  Kliknij przycisk **Start**, a następnie wybierz pozycję **Panelu sterowania**.  
  
    2.  W **Panelu sterowania**, wybierz **Przełącz do widoku klasycznego**, jeśli to konieczne, a następnie kliknij dwukrotnie **narzędzia administracyjne**.  
  
2.  W **narzędzia administracyjne** okna, kliknij dwukrotnie **Internet Information Services (IIS) Manager**.  
  
     Otwiera Menedżera usług IIS.  
  
3.  W **połączeń** okienku rozwiń \<nazwa komputera > węzła, jeśli to konieczne.  
  
4.  W obszarze \<nazwa komputera > węzeł, kliknij przycisk **pul aplikacji**.  
  
5.  W **pul aplikacji** listy, kliknij prawym przyciskiem myszy nazwę puli aplikacji jest uruchamiany w, a następnie kliknij przycisk **Zaawansowane ustawienia**.  
  
6.  W **Zaawansowane ustawienia** okno dialogowe Znajdź **Model procesu** sekcji, a następnie wykonaj jedną z następujących czynności:  
  
    -   Ustaw **włączone Ping** do **False**.  
  
    -   Ustaw **maksymalny czas odpowiedzi polecenia Ping** na wartość większą niż 90 sekund.  
  
     Ustawienie **włączone Ping** do **False** zatrzymuje IIS sprawdzanie, czy Proces roboczy jest nadal uruchomiona i przechowuje proces roboczy aktywności, aż do zatrzymania debugowanego procesu. Ustawienie **maksymalny czas odpowiedzi polecenia Ping** na dużą wartość Zezwala usługom IIS do dalszego monitorowania procesu roboczego.  
  
7.  Kliknij przycisk **OK** zamknąć **Zaawansowane ustawienia** okno dialogowe.  
  
8.  Zamknij Menedżera usług IIS i **narzędzia administracyjne** okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)