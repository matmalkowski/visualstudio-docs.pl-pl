---
title: 'Porady: Debugowanie aparatu debugowania niestandardowego | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a91dbb7797d69ec71b776eeef5e34e0ced21ad9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Porady: Debugowanie aparatu debugowania niestandardowych
Typ projektu uruchamia aparat debugowania (DE) z <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metody. Oznacza to, że DE jest uruchamiana pod kontrolą wystąpienia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kontrolowanie typu projektu. Jednak to wystąpienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie można debugować DE. Jakie następujące przedstawiono kroki, co pozwala na debugowanie z niestandardowych DE.  
  
> [!NOTE]
>  : W procedurze "Debugowanie niestandardowych debugowania aparatu" należy poczekać DE przed dołączeniem do niej. Jeśli okno komunikatu na początku Twojej DE, która pojawia się po uruchomieniu DE, możesz dołączyć w tym momencie, a następnie wyczyść pola wiadomości, aby kontynuować. W ten sposób można można przechwytywać wszystkie zdarzenia DE.  
  
> [!WARNING]
>  Musisz mieć zainstalowany przed rozpoczęciem poniższej procedury debugowania zdalnego. Zobacz [zdalnego debugowania](../../debugger/remote-debugging.md) szczegółowe informacje.  
  
### <a name="debugging-a-custom-debug-engine"></a>Debugowanie aparatu debugowania niestandardowych  
  
1.  Uruchomić msvsmon.exe, Monitor zdalnego debugowania.  
  
2.  Z **narzędzia** w msvsmon.exe, wybierz opcję menu **opcje** otworzyć **opcje** okno dialogowe.  
  
3.  Wybierz opcję "bez uwierzytelniania" i kliknij **OK**.  
  
4.  Uruchomić wystąpienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i otworzyć projekt DE niestandardowych.  
  
5.  Uruchom drugie wystąpienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i Otwórz projekt niestandardowych uruchamiająca DE (rozwoju, zazwyczaj jest to w gałęzi rejestru eksperymentalne skonfigurowany po zainstalowaniu VSIP).  
  
6.  W tym drugie wystąpienie parametru [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], załadować pliku źródłowego z niestandardowych projekt i uruchomić program do debugowania. Poczekaj kilka chwil, aby umożliwić DE załadować lub poczekaj, aż punkt przerwania zostaje trafiony.  
  
7.  W pierwszym wystąpieniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (z projektu DE), wybierz **dołączyć do procesu** z **debugowania** menu.  
  
8.  W **dołączyć do procesu** okno dialogowe, zmień **transportu** do **zdalnego (Native tylko z bez uwierzytelniania)**.  
  
9. Zmień **kwalifikator** do nazwy komputera (Uwaga: nie historię wpisów, dlatego należy wpisać tylko raz w tym nazwa).  
  
10. W **dostępne procesy** wybierz wystąpienie z DE, która jest uruchomiona i kliknij przycisk **Attach** przycisku.  
  
11. Po symbole zostały załadowane w Twojej DE, umieść punktów przerwania w kodzie DE.  
  
12. Za każdym razem, Zatrzymaj, a następnie ponownie uruchom proces debugowania, powtórz kroki od 6 do 10.  
  
### <a name="debugging-a-custom-project-type"></a>Debugowanie typu niestandardowego projektu  
  
1.  Uruchom [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w gałęzi rejestru normalne i obciążenia projektu wpisz projektu (jest to, źródła do danego typu projektu nie wystąpienia tego typu projektu).  
  
2.  Otwórz właściwości projektu i przejdź do **debugowania** strony. Aby uzyskać **polecenia**, wpisz ścieżkę do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (domyślnie jest to *[dysk]*\Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).  
  
3.  Aby uzyskać **argumenty polecenia**, typ `/rootsuffix exp` gałęzi rejestru eksperymentalne (utworzone podczas instalacji VSIP).  
  
4.  Kliknij przycisk **OK** aby zatwierdzić zmiany.  
  
5.  Naciśnij klawisz F5, aby uruchomić danego typu projektu. Spowoduje to uruchomienie drugie wystąpienie parametru [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6.  W tym momencie można umieścić punkty przerwania w kodzie źródłowym typu projektu.  
  
7.  W drugim wystąpieniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], obciążenia lub Utwórz nowe wystąpienie tego typu projektu. Podczas ładowania lub tworzenia napotkać punkty przerwań.  
  
8.  Debugowanie danego typu projektu.  
  
9. Jeśli zdecydujesz się na debugowanie tego procesu uruchamiania DE, można wykonać kroki opisane w procedurze "Debugowanie niestandardowych debugowania aparatu" można dołączyć do sieci DE po jej uruchomieniu. Zapewni to trzy wystąpienia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uruchomiona: jeden dla typu źródła danych projektu, drugie typu wystąpień projektu i podłączony do sieci DE innej.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aparat debugowania niestandardowych](../../extensibility/debugger/creating-a-custom-debug-engine.md)