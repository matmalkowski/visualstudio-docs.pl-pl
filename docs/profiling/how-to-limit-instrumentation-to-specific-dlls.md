---
title: "Porady: ograniczanie Instrumentacji do określonych bibliotek DLL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: performance tools, runtime profiling control window
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3ad8aaf7dbf9960a3281add90da685c2942bd179
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Porady: ograniczanie instrumentacji do określonych bibliotek DLL
Za pomocą metody profilowania instrumentacji, można ograniczyć zbierania danych profilowania do jednego lub więcej bibliotek DLL w aplikacji. Aby profil jednego lub więcej bibliotek DLL w aplikacji, należy utworzyć sesję wydajności, który zawiera pliki dll jako miejsca docelowe. Można określić bibliotek DLL, które mają być profilu jako projekty w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania lub jako niezależne pliki binarne.  
  
### <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Ograniczenie Instrumentacji do określonych bibliotek DLL w rozwiązaniu Visual Studio  
  
1.  Otwórz rozwiązanie, które zawiera biblioteki DLL w [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
2.  Na **Analizuj** menu, wybierz opcję **Uruchom Kreatora osiągów**.  
  
3.  Wybierz **Instrumentacji** metodę profilowania, a następnie kliknij przycisk **dalej**.  
  
4.  Z **które z następujących dostępnych elementów docelowych chcesz profil?**, wybierz nazwę projektu dll, a następnie kliknij przycisk **dalej**.  
  
5.  Kliknij przycisk **Zakończ** aby zakończyć działanie kreatora i wyświetlić nowej sesji wydajności w **Eksplorator wydajności** okna.  
  
6.  Kliknij prawym przyciskiem myszy **celów** , a następnie wybierz **Dodawanie projektu docelowego**.  
  
7.  Z **Dodawanie projektu docelowego** wybierz projekt wykonywalny, który ma być używany do wykonywania biblioteki DLL.  
  
     Opcjonalny. Wszystkie projekty biblioteki DLL, które mają można dodać do profilu.  
  
8.  Aby zapobiec zbierania danych dla dodany projekt, kliknij prawym przyciskiem myszy nazwę projektu, a następnie wyczyść **dokumentu** pole wyboru.  
  
### <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Aby określić określonych bibliotek DLL do profilu jako niezależne pliki binarne  
  
1.  Otwórz [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
2.  Na **Analizuj** menu, wybierz opcję **Uruchom Kreatora osiągów**.  
  
3.  Z **które z następujących dostępnych elementów docelowych chcesz profilu**, wybierz pozycję **profil biblioteki dołączanej dynamicznie (. Biblioteki DLL)** , a następnie kliknij przycisk **dalej**.  
  
4.  Na drugiej stronie kreatora wykonaj następujące czynności:  
  
    -   Wpisz ścieżkę i nazwę pliku dll, który ma zostać profilu w **ścieżka biblioteki Dll**. Można również kliknąć przycisk wielokropka (...), aby zlokalizować plik w **biblioteki dołączanej dynamicznie do profilowania** okno dialogowe. Należy pamiętać o konieczności podania kopię pliku .dll, który zostanie uruchomiony przy użyciu pliku wykonywalnego (.exe) obok wybranego.  
  
    -   Wpisz ścieżkę i nazwę pliku wykonywalnego (.exe), który wykonuje .dll w **ścieżka pliku wykonywalnego**. Można również kliknąć przycisk wielokropka (...), aby zlokalizować plik w **pliku wykonywalnego do uruchomienia** okno dialogowe.  
  
    -   Opcjonalny. Wpisz argumenty wiersza polecenia, które mają być przekazywane do pliku wykonywalnego w **argumenty wiersza polecenia**. Jeśli to konieczne, należy określić katalog roboczy dla aplikacji w **katalog roboczy**.  
  
    -   Kliknij przycisk **Dalej**.  
  
5.  Wybierz **Instrumentacji** metodę profilowania, a następnie kliknij przycisk **dalej**.  
  
6.  Kliknij przycisk **Zakończ** aby zakończyć działanie kreatora i wyświetlić nowej sesji wydajności w **Eksplorator wydajności** okna.  
  
7.  Opcjonalny. Aby dodać więcej plików dll, kliknij prawym przyciskiem myszy **celów** , a następnie wybierz **dodać docelowy binarne**. Wybierz pliki z **dodać docelowy binarne** okno dialogowe.  
  
    > [!NOTE]
    >  Nie należy określać plik wykonywalny (.exe), który korzysta z bibliotek DLL.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)   
 [Porady: ograniczanie Instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)