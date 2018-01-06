---
title: "Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 08/14/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3fbea34afa4e82ea360a0dfefe4f18dc74d11f19
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio
Można zastosować klucza produktu programowego jako część skrypt, który służy do automatyzowania wdrażania programu Visual Studio. Możesz ustawić klucz produktu na urządzeniu programowo podczas instalacji programu Visual Studio lub po zakończeniu instalacji.

## <a name="apply-the-license-after-installation"></a>Po zainstalowaniu Zastosuj licencji
 Zainstalowana wersja programu Visual Studio przy użyciu klucza produktu można aktywować przy użyciu `StorePID.exe` narzędzia na komputerach docelowych w trybie dyskretnym. `StorePID.exe`to narzędzie program, który instaluje z programu Visual Studio 2017 w następującej lokalizacji domyślnej: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Uruchom `StorePID.exe` z podwyższonym poziomem uprawnień, albo za pomocą agenta programu System Center lub wiersza polecenia o podniesionych uprawnieniach. Po nim za pomocą klucza produktu i kod produktu firmy Microsoft (MPC).

>[!IMPORTANT]
> Upewnij się uwzględnić kresek klucz produktu.

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 W poniższym przykładzie przedstawiono polecenie stosowania licencji dla programu Visual Studio Enterprise 2017, która ma MPC 08860, klucz produktu `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, przyjęto założenie, domyślna lokalizacja instalacji:

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 Poniższa tabela zawiera listę kodów MPC dla każdej wersji programu Visual Studio:

| Wersja programu Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Jeśli `StorePID.exe` pomyślnie zastosowanie klucza produktu, zwraca `%ERRORLEVEL%` 0. W przypadku wykrycia błędów, zwraca jedną z następujących kodów, w zależności od stanu błędu:

| Błąd                     | Kod |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:
* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi.
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio).  (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz też
 * [Instalowanie programu Visual Studio](../install/install-visual-studio.md)
 * [Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
