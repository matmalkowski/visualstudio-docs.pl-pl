---
title: 'Porady: ograniczanie Instrumentacji do określonych bibliotek DLL | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aefa0d5953d1e8d61615ac5bfe0af136082c96f3
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843952"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Porady: ograniczanie Instrumentacji do określonych bibliotek DLL

Za pomocą metody profilowania instrumentacji, można ograniczyć zbierania danych profilowania do jednego lub więcej bibliotek DLL w aplikacji. Aby profilu jeden lub więcej bibliotek DLL w aplikacji, należy utworzyć sesję wydajności, która obejmuje. *dll* pliki jako obiekty docelowe. Można określić bibliotek DLL, które chcesz profilu jako projekty w rozwiązaniu Visual Studio lub niezależne pliki binarne.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Ograniczenie Instrumentacji do określonych bibliotek DLL w rozwiązaniu Visual Studio

1. Otwórz rozwiązanie, które zawiera biblioteki DLL w programie Visual Studio.

2. Na **Analizuj** menu, wybierz opcję **Uruchom Kreatora osiągów**.

3. Wybierz **Instrumentacji** metodę profilowania, a następnie kliknij przycisk **dalej**.

4. Z **które z następujących dostępnych elementów docelowych chcesz profil?**, wybierz nazwę. *biblioteki dll* projektu, a następnie kliknij przycisk **dalej**.

5. Kliknij przycisk **Zakończ** aby zakończyć działanie kreatora i wyświetlić nowej sesji wydajności w **Eksplorator wydajności** okna.

6. Kliknij prawym przyciskiem myszy **celów** , a następnie wybierz **Dodawanie projektu docelowego**.

7. Z **Dodawanie projektu docelowego** wybierz projekt wykonywalny, który ma być używany do wykonywania biblioteki DLL.

     Opcjonalna. Wszystkie projekty biblioteki DLL, które mają można dodać do profilu.

8. Aby zapobiec zbierania danych dla dodany projekt, kliknij prawym przyciskiem myszy nazwę projektu, a następnie wyczyść **dokumentu** pole wyboru.

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Aby określić określonych bibliotek DLL do profilu jako niezależne pliki binarne

1. Otwórz program Visual Studio.

2. Na **Analizuj** menu, wybierz opcję **Uruchom Kreatora osiągów**.

3. Z **które z następujących dostępnych elementów docelowych chcesz profilu**, wybierz pozycję **profil biblioteki dołączanej dynamicznie (. Biblioteki DLL)** , a następnie kliknij przycisk **dalej**.

4. Na drugiej stronie kreatora wykonaj następujące czynności:

    - Wpisz ścieżkę i nazwę. *dll* pliku, który ma być profil **ścieżka biblioteki Dll**. Można również kliknąć przycisk wielokropka (...), aby zlokalizować plik w **biblioteki dołączanej dynamicznie do profilowania** okno dialogowe. Należy pamiętać, że należy określić kopię. *dll* pliku, który będzie można uruchomić pliku wykonywalnego (. *exe*) pliku, który wybrano obok.

    - Wpisz ścieżkę i nazwę pliku wykonywalnego (. *exe*) plików, które wykonują. *dll* w **ścieżka pliku wykonywalnego**. Można również kliknąć przycisk wielokropka (...), aby zlokalizować plik w **pliku wykonywalnego do uruchomienia** okno dialogowe.

    - Opcjonalna. Wpisz argumenty wiersza polecenia, które mają być przekazywane do pliku wykonywalnego w **argumenty wiersza polecenia**. Jeśli to konieczne, należy określić katalog roboczy dla aplikacji w **katalog roboczy**.

    - Kliknij przycisk **Dalej**.

5. Wybierz **Instrumentacji** metodę profilowania, a następnie kliknij przycisk **dalej**.

6. Kliknij przycisk **Zakończ** aby zakończyć działanie kreatora i wyświetlić nowej sesji wydajności w **Eksplorator wydajności** okna.

7. Opcjonalna. Aby dodać więcej. *dll* plików, kliknij prawym przyciskiem myszy **celów** , a następnie wybierz **dodać docelowy binarne**. Wybierz pliki z **dodać docelowy binarne** okno dialogowe.

    > [!NOTE]
    > Nie należy określać plik wykonywalny (. *exe*) pliku, który korzysta z bibliotek DLL.

## <a name="see-also"></a>Zobacz także

[Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)  
[Instrukcje: ograniczanie instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)