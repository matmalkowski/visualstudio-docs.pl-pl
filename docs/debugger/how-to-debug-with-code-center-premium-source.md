---
title: "Porady: debugowanie przy użyciu źródła Code Center Premium | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d7405deed95f14314215b869a02bcf8a1afddea2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Porady: debugowanie przy użyciu źródła Code Center Premium
Z [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] debugera, można debugować bezpiecznego udostępnionego źródła z Microsoft MSDN Code Center Premium.  
  
 W tym temacie wyjaśniono, jak skonfigurować i debugowania kodu źródła Code Center Premium w programie Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Aby przygotować się do debugowania z Code Center Premium  
  
1.  Połącz czytnika kart inteligentnych i włóż kartę uzyskanego z inicjatywy udostępnionego źródła.  
  
2.  Uruchom program Visual Studio.  
  
3.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
4.  W **opcje** po otwarciu okna dialogowego **debugowanie** węzeł i kliknij przycisk **ogólne**.  
  
5.  Wyczyść **Włącz opcję tylko mój kod (tylko zarządzane)** pole wyboru.  
  
6.  Wybierz **Włącz obsługę serwera źródłowego Włącz**.  
  
7.  Wyczyść **wymagają źródła dokładnej zgodności plików oryginalnej wersji**.  
  
8.  W obszarze **debugowanie** węzła, kliknij przycisk **symbole**.  
  
9. W **pliku symboli (.pdb) lokalizacje** zaznaczenie pola wyboru **symboli serwera Microsoft** pole wyboru i dodaj następujące lokalizacje:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Pamiętaj dołączyć końcowy ukośnik **/**  na końcu ścieżki.  
  
     Przenieś te lokalizacje na początku listy, aby upewnić się, czy pierwszy załadowano symbole te.  
  
    > [!NOTE]
    >  Musi być najpierw wymienione te lokalizacje Code Center Premium, dzięki czemu są one pierwszy lokalizacje, które zostały załadowane. W programie Visual Studio 2010, nie można przenieść serwerom powyżej **serwerów symboli firmy Microsoft** wpisu, dlatego należy wyczyścić pole wyboru.  
    >   
    >  Aby załadować symbole z symboli firmy Microsoft podczas sesji debugowania, wykonaj następujące czynności:  
    >   
    >  1.  Na **debugowania** menu, wybierz **Windows** , a następnie wybierz **modułów**.  
    > 2.  Wybierz moduł, który ma symboli dla elementu, a następnie otwórz menu skrótów. Wybierz **Załaduj symbole z** , a następnie wybierz **serwerów symboli firmy Microsoft**.  
  
10. W **pamięci podręcznej symboli z serwerów symboli w tym katalogu** wprowadź lokalizację, takich jak `C:\symbols` gdzie Code Center Premium można pamięci podręcznej symboli. Buforowanie symboli może znacznie poprawić wydajność podczas debugowania.  
  
     Jeśli wystąpią problemy debugowania kodu źródłowego z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] po ukończeniu tej procedury Sprawdź Twojej lokalizacji pamięci podręcznej plików symboli wcześniej pamięci podręcznej i przestarzałe. Usuń pliki symboli nieaktualne.  
  
11. Kliknij przycisk **OK**.  
  
12. Uruchom ponownie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aby upewnić się, że ustawienia są zachowywane.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Debugowanie kodu źródłowego przy użyciu dołączanie do procesu  
  
1.  Połącz czytnika kart inteligentnych i włóż kartę uzyskanego z inicjatywy udostępnionego źródła.  
  
2.  Uruchom program Visual Studio.  
  
3.  Otwórz projekt programu Visual Studio.  
  
4.  Na **narzędzia** menu, kliknij przycisk **dołączyć do procesu**.  
  
5.  W **dołączyć do procesu** okno dialogowe, kliknij przycisk **wybierz**.  
  
6.  W **wybór typu kodu** okna dialogowego, w obszarze **wykrywa te typy kodu**, wybierz pozycję **natywnego**, **zarządzane**, i **zarządzane ( wersja 4.0)**.  
  
7.  Kliknij przycisk **OK** aby odrzucić **wybór typu kodu** okno dialogowe.  
  
8.  W **dostępne procesy** wybierz proces, który chcesz debugować.  
  
9. Kliknij przycisk **dołączyć**.  
  
10. Po wyświetleniu monitu o potwierdzenie tego certyfikatu, kliknij przycisk **OK**. Następnie wprowadź numer PIN. Zaakceptuj warunki użytkowania Code Center Premium, jeśli zostanie wyświetlony monit.  
  
     Pobieranie symboli może trwać bardzo długo, w zależności od szybkości sieci. Pasek stanu wskaże, gdy wszystkie symbole zostały pomyślnie pobrane.  
  
11. Powtórz kroki dołączania dla wszystkich zarządzanych projektów w rozwiązaniu.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Do debugowania kodu źródłowego z istniejącego rozwiązania  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla rozwiązania, a następnie wybierz pozycję **właściwości**.  
  
2.  W oknie dialogowym strony właściwości rozwiązania wybierz **debugowania plików źródłowych** w **wspólne właściwości** węzła.  
  
3.  Dodaj następującej lokalizacji w celu **katalogów zawierający pliki źródłowe** listy:  
  
     `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Pamiętaj dołączyć końcowy ukośnik **/**  na końcu ścieżki.  
  
4.  Dla każdego zarządzanego projektu w rozwiązaniu wykonaj następujące czynności  
  
    1.  W Eksploratorze rozwiązań Otwórz menu skrótów projektu, a następnie wybierz pozycję **właściwości**.  
  
    2.  Wybierz **debugowania** , a następnie wybierz **Włącz debugowanie kodu niezarządzanego**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Aby debugować rozwiązania przy użyciu źródła Code Center Premium  
  
1.  W Twojej `Package` klasy, należy ustawić punkt przerwania w Konstruktorze pakietu.  
  
2.  W `Debug` menu, kliknij przycisk **Rozpocznij debugowanie**.  
  
3.  Po trafieniu punktu przerwania w Konstruktorze pakietu, przejdź do **stos wywołań** oknie i kliknij prawym przyciskiem myszy ramki stosu zestawu chcesz załadować symboli, następnie kliknij przycisk **załadować symbole**.  
  
     Kliknij dwukrotnie ramki wywołań można załadować źródła.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Aby przejrzeć kod źródłowy w Code Center Premium  
  
1.  Połącz czytnika kart inteligentnych i włóż kartę uzyskanego z inicjatywy udostępnionego źródła.  
  
2.  Uruchom Internet Explorer wprowadź następujący adres URL:`https://codepremium.msdn.microsoft.com`  
  
3.  Przeglądaj w poszukiwaniu źródła, które ma.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)