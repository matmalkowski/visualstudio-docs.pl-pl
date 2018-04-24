---
title: Debugowanie za pomocą prefetched zawartości w aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 241937c8462577d6af375d2440efe828a738a8cc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Debugowanie aplikacji platformy uniwersalnej systemu Windows przy użyciu prefetched zawartości w programie Visual Studio
  
 Aby zapewnić poprawę reakcji aplikacji platformy uniwersalnej systemu Windows, możesz poprosić o wstępnie zawartość sieci web, takich jak strony sieci web lub obrazów, do aplikacji z systemem Windows [WinINet](http://msdn.microsoft.com/library/0a06f2af-957a-4dff-a8cc-187370181b5c) pamięci podręcznej. Ta funkcja jest wywoływana odczyt z wyprzedzeniem. Jest szczególnie użyteczna, dla zawartości, która jest używana podczas uruchamiania, ale użytkownik może zawartość pobrana z wyprzedzeniem inne często używane, za. Metody [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) klasy pozwalają określić identyfikatory URI zawartości, którą chcesz wstępnie. Zobacz zestaw Windows SDK [przykładowej zawartości pobierania z wyprzedzeniem](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) przykłady sposobu dodawania funkcji ContentPrefetcher do aplikacji.  
  
 System Windows używa algorytmu heurystycznego, aby określić, gdy a odczyt z wyprzedzeniem powinna się odbyć i zasobów, do których zostaną pobrane. Algorytm heurystyczny uwzględniać konta systemu sieci i stan zasilania, historii użycia aplikacji użytkownika i liczbę prób uprzedniego pobierania z wyprzedzeniem. W programie Visual Studio, można użyć **wyprzedzeniem aplikacji Sklepu Windows wyzwalacza** polecenie, aby wymusić systemu Windows, aby zignorować heurystyki ContentPrefetcher i wstępnie całej zawartości sieci web określonego. Może to być przydatne w przypadku testowania aplikacji zachowanie lub wydajności ze zawartością pobrana z wyprzedzeniem w znanego stanu (załadowany lub nie jest załadowany).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Aby wymusić wstępne ładowanie ContentPrefetcher określone zasoby  
 Tej procedurze przyjęto założenie, że masz już Ustawianie funkcji ContentPrefetcher i określony identyfikator URI zawartości do wstępnego w projekcie aplikacji. Aby wymusić wstępnego ładowania zawartości, gdy określone zasoby są nowe lub zmodyfikowane, należy uruchomić i zatrzymać aplikację przed wybraniem **wyprzedzeniem aplikacji Sklepu Windows wyzwalacza** polecenia. Możesz uruchomić aplikację, aby najpierw zarejestrować identyfikatory URI. **Wyzwalanie pobierania z wyprzedzeniem aplikacji Sklepu Windows** polecenia następnie wymusza ContentPrefetcher do pobrania zawartości i dodaj ją w pamięci podręcznej. W kolejnych uruchomieniach aplikacji można założyć, że zawartość jest wstępnie załadowane.  
  
1.  Uruchamiają aplikację, aby zarejestrować zawartość pobierania z wyprzedzeniem identyfikatorów URI z aplikacją. Na **debugowania** menu, wybierz **Rozpocznij debugowanie** (skrót klawiaturowy: F5).  
  
2.  Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (skrót klawiaturowy: Shift + F5).  
  
3.  Na **debugowania** menu, wybierz **innych celów debugowania** , a następnie wybierz **wyprzedzeniem aplikacji Sklepu Windows wyzwalacza**.  
  
 Można teraz debugowania, testów lub analizy aplikacji z zasobami prefetched sieci web.  
  
> [!NOTE]
>  Powtórz te czynności w miarę dodawania lub modyfikowania zawartości sieci web określonego.  
  
## <a name="see-also"></a>Zobacz też  
 [Wpis w blogu: wyzwalanie pobierania z wyprzedzeniem dla aplikacji ze Sklepu Windows w programie Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)