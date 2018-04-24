---
title: 'Porady: Ustawianie uprawnień | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1f3cf4ca3cb79a6b58d4f3549d05d355764148f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-set-permissions"></a>Porady: Ustawianie uprawnień

W tym artykule opisano, jak Administrator komputera przyznaje uprawnienia zabezpieczeń wymagane do profilowania do użytkownika lub grupę, która nie ma uprawnień administratora na tym komputerze.

Zasady zabezpieczeń podstawowych stany aplikacje powinny być uruchamiane z nie więcej niż uprawnienia, które są im potrzebne. Ta zasada dotyczy również użytkowników. Jeśli użytkownicy mogą być skuteczne, gdy jest zalogowany jako członków grupy użytkowników zamiast do grupy administratorów, ich nie należy przyznawać uprawnienia administratora. Pierwsza procedura "Aby utworzyć konto użytkownika, które ma uprawnienia użytkownika" zawiera opis sposobu tworzenia konta użytkownika dla elementu członkowskiego do grupy użytkowników.

Członkowie grupy Użytkownicy wymaga dostępu do folderów i plików na dysku, które są udostępniane innym członkom zespołu. Druga procedura "Aby udzielić dostępu do plików projektu udostępnionego" opisuje sposób przyznania dostępu.

Członkowie grupy użytkowników można uruchomić narzędzi profilowania, jeśli administrator przyznał im dostęp do sterownika oprogramowania dla narzędzi profilowania. Ostatniej procedury "Aby udzielić dostępu do profilowania sterownik" opisano, jak uzyskać dostęp do tego sterownika.

> [!NOTE]
> Musisz mieć uprawnienia administratora, które należy wykonać czynności opisane w tych procedurach.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>Aby utworzyć konto użytkownika, które ma uprawnienia użytkownika

1. Kliknij prawym przyciskiem myszy **Mój komputer** , a następnie kliknij przycisk **Zarządzaj**.

     **Zarządzanie komputerem** zostanie otwarte okno.

2. Rozwiń węzeł **lokalnych użytkowników i grup**.

3. Kliknij prawym przyciskiem myszy **użytkowników** folder, a następnie kliknij przycisk **nowego użytkownika**.

     **Nowego użytkownika** zostanie wyświetlone okno dialogowe.

4. Wypełnij pola w oknie dialogowym z informacjami dla konta użytkownika, które tworzysz. Określ hasło. Opcjonalnie zaznacz pole wyboru, które wymaga, aby zmiany hasła przy następnym logowaniu użytkownika.

5. Kliknij przycisk **Utwórz** , a następnie kliknij przycisk **Zamknij**.

     Nowy użytkownik pojawi się w grupie Użytkownicy, grupy użytkowników, którzy nie mają uprawnień administratora.

## <a name="to-grant-access-to-shared-project-files"></a>Aby udzielić dostępu do udostępnionych plików projektu

1. W Eksploratorze Windows (lub Eksploratora plików) Znajdź korzeń drzewa folder dla projektu pliki używane przez tego użytkownika i udostępnionych przez zespół projektu.

     Ścieżka tego folderu może wyglądać w następujący sposób:

    ```
    D:\ourProject
    ```

2. Kliknij prawym przyciskiem myszy folder, a następnie kliknij przycisk **właściwości**.

     **\<Nazwa folderu > właściwości** zostanie wyświetlone okno dialogowe.

3. Kliknij przycisk **zabezpieczeń** kartę.

4. Kliknij nazwę konta użytkownika w **nazwy grup lub użytkowników** pole.

5. W **uprawnienia dla \<nazwa użytkownika >** zaznacz pole wyboru **Pełna kontrola**.

6. Kliknij przycisk **OK**.

     Spowoduje to przydzielenie uprawnień dla użytkownika na drzewie folderu udostępnionego, który rozpoczyna się od wybrany w kroku 5 folder.

## <a name="to-grant-access-to-the-profiling-driver"></a>Aby udzielić dostępu do profilowania sterownika

1. Otwórz wiersz polecenia jako administrator.

2. Zmień katalog na:

    ```
    <drive>:\Program Files\Microsoft Visual Studio 10\Team Tools\Performance Tools
    ```

3. Uruchom następujące polecenie:

    ```
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     To polecenie instaluje i uruchamia sterownik dla narzędzi profilowania.

     To polecenie uruchamia profilowanie sterowników i usługi, aby użytkownicy inni niż administratorzy mogą używać profilowania funkcji, które są dostępne w obszarze procesu ich użytkownika. Tylko Administrator może uruchomić polecenie; i kończy się niepowodzeniem dla użytkowników innych niż administracyjne.

     Należy zauważyć, że efekty w tym kroku są cofnięte po ponownym uruchomieniu komputera, chyba że również wykonania ostatniego kroku tej procedury.

4. Uruchom polecenie, aby zezwolić na dostęp do profilowania funkcji sterownika przez użytkownika lub grupę, która nie ma dostępu administratora do komputera:

    ```
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     To polecenie przyznaje \<nazwa użytkownika > lub \<Nazwa grupy > konto dostępu do narzędzi profilowania. \<Prawo > Opcja określa profilowania funkcji użytkownik może uzyskać dostęp. \<Prawo > opcja może być co najmniej jeden z następujących wartości:

    - FullAccess — zezwala na dostęp do wszystkich metod profilowania zbieranie danych wydajności z usługi, w tym próbkowania i profilowania międzysesyjnego.

    - SampleProfiling — zezwala na dostęp do przykładowej metod profilowania

    - CrossSession — zezwala na dostęp do wielu sesji profilowania, która jest wymagana dla usługi profilowania.

5. (Opcjonalnie) Aby zachować wyniki poprzednie kroki, po ponownym uruchomieniu komputera, uruchom następujące polecenie:

    ```
    vsperfcmd /admin:driver,autostart,on
    ```

 Określeni użytkownicy po zalogowaniu, teraz będzie konieczne użycie narzędzi profilowania bez uprawnień administratora.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
[VSPerfCmd](../profiling/vsperfcmd.md)  
[Profilowanie i bezpieczeństwo systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md)