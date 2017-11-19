---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 27cff46f5a68ef28f247aa159a2b8be5db56b0fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
Jeśli zainstalowano za pomocą Instalatora platformy sieci Web narzędzia Web Deploy, można wdrożyć aplikacji bezpośrednio z programu Visual Studio.

1. Uruchom program Visual Studio z uprawnieniami administratora, a następnie ponownie otwórz projekt.

    Wymagane są uprawnienia administratora do wdrożenia aplikacji za pomocą narzędzia Web Deploy.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **publikowania**.

3. Dla **wybierz cel publikowania**, wybierz pozycję **usług IIS, FTP, itp.** i kliknij przycisk **publikowania**.

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

4. Wprowadź parametry konfiguracji korekty ustawień usług IIS.

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Jeśli nie jest rozpoznawane nazwy hosta podczas sprawdzania poprawności w kolejnych kroków w **serwera** tekst pola, spróbuj adresu IP. Obejmują `http://` jako prefiksu w **serwera** pola.  Upewnij się, że korzystanie z portu 80 w **serwera** tekst pole i upewnij się, że port 80 jest otwarty w zaporze.

6. Kliknij przycisk **dalej**, wybierz **debugowania** konfiguracji i wybierz polecenie **Usuń dodatkowe pliki w miejscu docelowym** w obszarze **publikowania pliku** Opcje.

    > [!NOTE]
    > Jeśli wybierzesz konfiguracji wydania, można wyłączyć debugowania w pliku web.config podczas publikowania.

5. Kliknij przycisk **Prev**, a następnie wybierz pozycję **weryfikacji**. Sprawdza ustawienia połączenia, możesz opublikować.

6. Kliknij przycisk **publikowania** do publikowania aplikacji.

    Karta danych wyjściowych zawiera, jeśli publikowanie zakończy się pomyślnie, a następnie otwarciu aplikacji przeglądarki sieci.

    Jeśli wystąpi błąd zauważyć narzędzia Web Deploy, sprawdź ponownie kroki instalacji narzędzia Web Deploy i upewnij się, że są otwarte porty (Web Deploy wymaga także portu 8172 być otwarte na serwerze).

    Jeśli aplikacja wdraża się pomyślnie, ale nie działa poprawnie, może to być problem z konfiguracji usług IIS, instalacja programu ASP.NET lub konfigurację witryny sieci Web. W systemie Windows Server otwórz witrynę sieci Web za pomocą programu IIS, aby uzyskać bardziej szczegółowe komunikaty o błędach, a następnie ponownie sprawdzić wcześniejszych krokach.