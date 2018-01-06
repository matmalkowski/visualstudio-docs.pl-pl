---
title: Przechwytywanie informacji graficznych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/09/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
caps.latest.revision: "41"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 89488533ab8ba36b0344faa7f0b800d8c4ecc6ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych
Przechwytywanie informacji graficznych z aplikacji Direct3D, aby mogli używać analizatora grafiki programu Visual Studio, aby zdiagnozować problemy z renderowaniem i problemy z wydajnością.  
  
## <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych  
 Przechwytywanie informacji graficznych jest procesem dwuetapowym. Po pierwsze, uruchom aplikację w obszarze Diagnostyka grafiki, a następnie określ jedną lub więcej ramek, z których zostaną przechwycone szczegółowe informacje.  
  
### <a name="to-run-your-app-under-graphics-diagnostics"></a>Aby uruchomić aplikację w obszarze Diagnostyka grafiki  
  
-   Na pasku menu wybierz **debugowania**, **grafiki**, **Rozpocznij debugowanie grafiki**. (Klawiatura: naciśnij klawisze Alt+F5)  
  
-   Na **grafiki** narzędzi wybierz **Rozpocznij debugowanie grafiki** przycisku.  
  
 Gdy aplikacja jest uruchomiona w ramach diagnostyki grafiki, pewne rodzaje informacji graficznych są cały czas przechwytywane; obejmuje to konfigurację urządzenia, tworzenie łańcucha wymiany elementów, tworzenie grafiki, obiektów i zasobów oraz inne ważne wydarzenia, które wpływają na więcej niż jedną klatkę. W tym samym czasie można przechwycić szczegółowe informacje na temat konkretnych klatek. Dotyczy to wywołania rysowań i wysyłań cieniowania obliczenia, wraz z obiektami i zasobami Direct3D, które je obsługują.  
  
### <a name="to-capture-a-frame"></a>Aby przechwycić ramkę  
  
-   W programie Visual Studio na **grafiki** narzędzi, kliknij przycisk **przechwycić ramki** przycisk ![ikonę przycisku przechwytywania grafiki](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").  
  
-   Na klawiaturze naciśnij klawisz Print Screen.
  
    > [!NOTE]
    >  Gdy aplikacja działa w ramach **diagnostyki grafiki**, tylko można używać klawisza Print Screen Aby przechwycić ramkę informacji graficznych, nie wykonać jego normalne działanie. To pozostaje, dopóki nie zatrzymasz przechwytywania informacji graficznych — zwykle przez zatrzymanie debugowania lub normalne wyjście z aplikacji — nawet wtedy, gdy fokus jest na innej aplikacji.  
  
-   W interfejsie przechwytywania programu Visual Studio, wybierz **przechwycić ramki** przycisk znajdujący się poniżej **sesji diagnostycznej** osi czasu, lub wybierz duża **przechwycić ramki** przycisku znajduje się poniżej **klatek na sekundę** pływackiej lane i w prawo ramek wcześniej przechwycone. Przyciski zostały wyróżnione na poniższym obrazie.  
  
     ![Przechwycić ramki za pomocą narzędzia użycie procesora GPU.](media/pix_gpu_usage_tool_capture_frame.png)  
  
     Jeśli wszystko jest gotowe do sprawdzenia ramki zostało przechwycone, uruchomić **analizatora grafiki programu Visual Studio** wykonując **ramek...**  łącze powyżej obraz miniatury lub klikając dwukrotnie miniaturę.  
  
 Można przechwycić tylko całe ramki, więc po zainicjowaniu przechwytywania, że to naprawdę informacji graficznych z następnej ramki, który jest zarejestrowany. Zapisywanie rozpoczyna się natychmiast po zaprezentowaniu klatki, w której rozpocząłeś przechwytywanie, i kończy się po zaprezentowaniu przechwyconej klatki. Możesz przechwycić tyle klatek, ile chcesz, gdy aplikacja jest uruchomiona w ramach diagnostyki grafiki. Jeśli nie przechwycisz żadnej ramki, dziennik grafiki jest odrzucany.  
  
 Podczas przechwytywania ramek, Visual Studio Wyświetla okno diagnostyki sesji (.diagsession). Jeśli zamknąć to okno, Zatrzymaj debugowanie lub zamknij aplikację, nie można przechwycić ramek więcej w tym dzienniku. Aby przechwycić więcej informacji graficznych, należy uruchomić aplikację pod nadzorem diagnostyki grafiki ponownie, aby uruchomić nową sesję diagnostyki.  
  
### <a name="graphics-diagnostics-capture-options"></a>Opcje przechwytywania danych diagnostycznych grafiki  
 Można skonfigurować przechwytywania zbieranie stosy wywołań dla wszystkich zdarzeń grafiki lub podzbiór ograniczone, wyłącz Przechwytywanie HUD i włączyć lub wyłączyć tryb zgodności przechwytywania.  
  
#### <a name="to-configure-graphics-diagnostics-capture-options"></a>Aby skonfigurować opcje przechwytywania diagnostyki grafiki  
  
1.  Na pasku menu wybierz menu Narzędzia, opcje. Zostanie wyświetlone okno dialogowe Opcje.  
  
2.  Na liście Kategoria opcje po lewej stronie wybierz diagnostyki grafiki, a następnie skonfiguruj żądane opcje diagnostyki grafiki.  
  
     **Zbieraj stosy wywołań podczas przechwytywania (zwalnia przechwytywanie)**  
     Zaznacz to pole, aby zbierać stosy wywołań. Stosy wywołań domyślnie nie są zbierane. Do przechwytywania stosy wywołań, upewnij się, że **stosów zbieranie wywołań podczas przechwytywania (zwalnia Przechwytywanie** ustawiono pole wyboru Włącz kolekcji, a następnie ustaw albo **rysowania, wysyłania obecna i wydajności znaczników**opcji (ustawienie domyślne) do zbierania tylko najważniejsze stosy wywołań, lub **dla wszystkich** opcję, aby zbierać wszystkie stosy wywołań. Aby zatrzymać zbieranie stosy wywołań później, należy wyczyścić **stosów zbieranie wywołań podczas przechwytywania (zwalnia Przechwytywanie** wyboru.  
  
     **Wyłącz HUD w grze podczas przechwytywania**  
     Sprawdź, czy to pole, aby wyłączyć HUD nakładki aplikację do uruchamiania grafiki diagnostyki zwykle wyświetla. Usuń jej zaznaczenie, aby wyświetlić nakładki HUD.  
  
     **Przechwyć w trybie zgodności**  
     Zaznacz to pole, aby przechwytywanie informacji graficznych w trybie zgodności. Przechwytywanie w trybie zgodności jest ustawieniem domyślnym. W trybie zgodności Direct3D nie będą zgłaszać czy procesora GPU obsługuje nowych funkcji poza tymi zdefiniowanymi w podstawowej funkcji na poziomie. To zapobiega aplikacji są przechwytywane z za pomocą rozszerzenia specyficzne dla sprzętu jego przechwyconych GPU na i zapewnia, że można odtwarzać dziennika grafiki przy użyciu dowolnego procesora GPU, który obsługuje funkcję tego samego lub wyższego poziomu. Usuń zaznaczenie tego pola, aby wyłączyć tryb zgodności; Dzienniki przechwycić przy wyłączono tryb zgodności zakończy się niepowodzeniem odtworzyć na dowolnym procesora GPU, który nie obsługuje tej samej dodatkowe funkcje, które były używane przez aplikację podczas przechwytywania.  
  
     **Zatrzymaj przechwytywanie, jeśli znaleziono błędy warstwy zestawu SDK**  
     Zaznacz to pole, aby natychmiast zatrzymać przechwytywanie, jeśli występują błędy.  
  
## <a name="capturing-graphics-information-remotely"></a>Zdalne przechwytywanie informacji graficznych  
 Informacje graficzne mogą być przechwytywane z aplikacji, która jest uruchomiona na komputerze lokalnym lub na zdalnym komputerze lub urządzeniu. Zdalnego przechwytywania jest obsługiwana w przypadku [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)] maszyn i [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)] urządzeń. Aby przechwytywać informacje graficzne z aplikacji, która jest uruchomiona zdalnie, skonfiguruj projekt dla zdalnego debugowania, a następnie uruchom aplikację w obszarze Diagnostyka grafiki zgodnie z wcześniejszym opisem. Aplikacja jest uruchamiana na komputerze zdalnym, a przechwycone informacje graficzne są rejestrowane na komputerze deweloperskim.  
  
 Konfiguracja projektu dla zdalnego debugowania zależy od rodzaju aplikacji, którą projektujesz, i języka programowania, którego używasz. Aby uzyskać informacje o sposobie konfigurowania zdalnego debugowania dla aplikacji platformy uniwersalnej systemu Windows, zobacz [aplikacji platformy uniwersalnej systemu Windows uruchom na komputerze zdalnym](../run-windows-store-apps-on-a-remote-machine.md). Aby uzyskać informacje o sposobie konfigurowania zdalnego debugowania aplikacji pulpitu systemu Windows, zobacz [zdalnego debugowania](../remote-debugging.md).  
  
 Później można użyć zdalnego komputera lub urządzenia do odtwarzania informacji graficznych, bez względu na to, gdzie informacje zostały przechwycone. Aby uzyskać więcej informacji, zobacz [porady: zmiana maszyny odtwarzania diagnostyki grafiki](how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="capturing-graphics-information-from-the-command-line"></a>Przechwytywanie informacji graficznych z wiersza polecenia  
 Informacji graficznych można przechwycić z aplikacji za pomocą narzędzia wiersza polecenia. To narzędzie DXCap.exe, można szybko przechwytywania i odtwarzać informacji graficznych bez korzystania z programu Visual Studio i przechwycenie programowe. W szczególności można użyć DXCap.exe automatyzacji lub w środowisku testowym. Aby uzyskać więcej informacji o DXCap.exe, zobacz [przechwytywania narzędzie wiersza polecenia](command-line-capture-tool.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: przechwytywanie informacji graficznych](walkthrough-capturing-graphics-information.md)