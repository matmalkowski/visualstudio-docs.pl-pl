---
title: Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio
description: Informacje o sposobie używania parametrów wiersza polecenia, aby kontrolować lub dostosować instalację programu Visual Studio.
ms.custom: ''
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3369fde3a9363951bf08b7af04ed35afc38a45c5
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio 2017 r.

Po zainstalowaniu programu Visual Studio 2017 z wiersza polecenia, można użyć różnych parametrów wiersza polecenia kontroli lub dostosowanie instalacji. W wierszu polecenia można wykonywać następujące czynności:

- Rozpocznij instalację z określonymi opcjami wstępnie wybrane.
- Zautomatyzowanie procesu instalacji.
- Tworzenie pamięci podręcznej (układ) plików instalacji do późniejszego użycia.

Opcje wiersza polecenia są używane w połączeniu z program inicjujący Instalatora, czyli pliku małych (około 1MB), który inicjuje proces pobierania. Program inicjujący jest pierwszy plik wykonywalny, który jest uruchamiany, gdy można pobrać z witryny programu Visual Studio. Aby uzyskać bezpośredniego łącza do najnowszej wersji inicjujący dla wersji produktu, który jest instalowany, użyj następujących łączy:

* [Visual Studio 2017 Enterprise](https://aka.ms/vs/15/release/vs_enterprise.exe)
* [Visual Studio 2017 Professional](https://aka.ms/vs/15/release/vs_professional.exe)
* [Visual Studio 2017 Community](https://aka.ms/vs/15/release/vs_community.exe)

## <a name="list-of-command-line-parameters"></a>Lista parametrów wiersza polecenia

 Visual Studio parametry wiersza polecenia jest rozróżniana wielkość liter.

> Składnia: `vs_enterprise.exe [command] <options>...`

(Zastąp `vs_enterprise.exe` odpowiednio dla wersji produktu instalujesz.)

>[!TIP]
> Więcej przykładów dotyczących sposobu instalacji programu Visual Studio 2017 za pomocą wiersza polecenia, zobacz [przykłady parametru wiersza polecenia](command-line-parameter-examples.md) strony.)

| **polecenie** | **Opis** |
| ----------------------- | --------------- |
| (pusty) | Instaluje produkt. |
| `modify` | Modyfikuje zainstalowany produkt. |
| `update` | Aktualizuje zainstalowany produkt. |
| `repair` | Naprawia zainstalowany produkt. |
| `uninstall` | Odinstalowuje zainstalowany produkt. |

| **Opcję instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Katalog instalacyjny dla wystąpienia działanie. W przypadku polecenia install jest **opcjonalnie** i gdzie zostaną zainstalowane wystąpienie. W przypadku innych poleceń jest **wymagane** i zainstalowanym uprzednio zainstalowanego wystąpienia. |
| `--addProductLang <language-locale>` | **Opcjonalne**: podczas instalacji lub zmodyfikować operacji, określa pakiety językowe interfejsu użytkownika, które są zainstalowane do tego produktu. Wiele razy może być wyświetlany w wierszu polecenia, aby dodać wiele pakietów językowych. Jeśli nie istnieje, instalacja korzysta z ustawień regionalnych komputera. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--removeProductLang <language-locale>` | **Opcjonalne**: podczas instalacji lub zmodyfikować operacji, określa pakiety językowe interfejsu użytkownika, które mają zostać usunięte z produktu. Wiele razy może być wyświetlany w wierszu polecenia, aby dodać wiele pakietów językowych. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalne**: obciążenia lub identyfikatory składników do dodania. Zainstalowano składniki wymagane artefaktu, ale nie zalecane lub opcjonalne składniki. Można kontrolować dodatkowe składniki za pomocą `--includeRecommended` i/lub `--includeOptional`. Precyzyjny system kontroli, możesz dołączyć `;includeRecommended` lub `;includeOptional` dla identyfikatora (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeRecommended;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. Ta opcja, w razie potrzeby można powtórzyć.|
| `--remove <one or more workload or component IDs>` | **Opcjonalne**: obciążenia lub identyfikatory składników do usunięcia. Aby uzyskać więcej informacji, zobacz nasze [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. Ta opcja, w razie potrzeby można powtórzyć.|
| `--in <path>` | **Opcjonalne**: identyfikator URI lub ścieżka do pliku odpowiedzi.  |
| `--all` | **Opcjonalne**: Określa, czy zainstalować obciążeń i wszystkie składniki produktu. |
| `--allWorkloads` | **Opcjonalne**: instaluje obciążeń i wszystkie składniki, żadne składniki opcjonalne lub zalecane. |
| `--includeRecommended` | **Opcjonalne**: zawiera składniki zalecane dla dowolnych zadań, które są zainstalowane, ale nie składników opcjonalnych. Obciążenia są określone za pomocą `--allWorkloads` lub `--add`. |
| `--includeOptional` | **Opcjonalne**: zawiera składniki opcjonalne dla dowolnych zadań, które są zainstalowane, ale nie zalecane składniki. Obciążenia są określone za pomocą `--allWorkloads` lub `--add`.  |
| `--quiet, -q` | **Opcjonalne**: interfejs użytkownika nie są wyświetlane podczas przeprowadzania instalacji. |
| `--passive, -p` | **Opcjonalne**: wyświetlanie interfejsu użytkownika, ale nie Żądaj interakcji użytkownika. |
| `--norestart` | **Opcjonalne**: Jeśli jest obecny, poleceń z `--passive` lub `--quiet` nie uruchamia ponownie komputer (w razie potrzeby).  To jest ignorowana, jeśli żadna `--passive` ani `--quiet` zostały określone.  |
| `--nickname <name>` | **Opcjonalne**: definiuje pseudonim można przypisać do zainstalowany produkt. Pseudonim nie może być dłuższa niż 10 znaków.  |
| `--productKey` | **Opcjonalne**: Określa klucz produktu do użycia na potrzeby zainstalowany produkt. Składa się z 25 alfanumeryczne znaki w formacie `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` lub `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Wyświetlanie w trybie offline wersję tej strony. |

> Uwaga: W przypadku określania wielu obciążeń i składników, należy powtórzyć `--add` lub `--remove` przełącznik wiersza polecenia dla każdego elementu.

| **Opcje układu** | **Opis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Określa katalog można utworzyć w trybie offline Zainstaluj pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [utworzyć sieciowej instalację programu Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Opcjonalne**: używane z `--layout` przygotować w trybie offline Zainstaluj pamięci podręcznej z pakietów zasobów z określonego języki. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalne**: obciążenia lub identyfikatory składników do dodania. Zainstalowano składniki wymagane artefaktu, ale nie zalecane lub opcjonalne składniki. Można kontrolować dodatkowe składniki za pomocą `--includeRecommended` i/lub `--includeOptional`. Precyzyjny system kontroli, możesz dołączyć `;includeRecommended` lub `;includeOptional` dla identyfikatora (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. <br/>**Uwaga**: Jeśli `--add` jest używana, tylko określonym obciążeń i składników oraz ich zależności zostaną pobrane. Jeśli `--add` nie zostanie określony, obciążeń i wszystkie składniki są pobierane do układu.|
| `--includeRecommended` | **Opcjonalne**: zawiera składniki zalecane dla dowolnych zadań, które są zainstalowane, ale nie składników opcjonalnych. Obciążenia są określone za pomocą `--allWorkloads` lub `--add`. |
| `--includeOptional` | **Opcjonalne**: zawiera zalecanej *i* opcjonalne składniki wszystkie obciążenia są uwzględniane w układzie. Obciążenia są określane za pomocą `--add`.  |
| `--keepLayoutVersion` | **Nowość w 15 ustęp 3, opcjonalnie**: zmiany układu bez aktualizowania wersji układu. |
| `--verify` | **Nowość w 15 ustęp 3, opcjonalnie**: Sprawdź zawartość układ. Pliki uszkodzone lub brakujące są wyświetlane. |
| `--fix` | **Nowość w 15 ustęp 3, opcjonalnie**: Sprawdź zawartość układ.  Jeśli pliki znajdują się być uszkodzony lub nie ma, są ponownego pobrania ich. Dostęp do Internetu jest wymagana do napraw układ. |
| `--clean <one or more paths to catalogs>` | **Nowość w 15 ustęp 3, opcjonalnie**: usuwa stare wersje składników z układu, który został zaktualizowany do nowszej wersji. |

| **Opcje zaawansowane instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcjonalne**: identyfikator dla tego wystąpienia kanału do zainstalowania. Jest to wymagane dla polecenia install ignorowany dla innych poleceń, jeśli `--installPath` jest określona. |
| `--channelUri <uri>` | **Opcjonalne**: identyfikator URI kanału manifestu. Jeśli aktualizacje nie są potrzebne, `--channelUri` może wskazywać na plik nie istnieje. (na przykład--channelUri C:\doesntExist.chman) Może być używany dla polecenia install; jest on ignorowany dla innych poleceń. |
| `--installChannelUri <uri>` | **Opcjonalne**: identyfikator URI kanału manifestu do użycia podczas instalacji. Identyfikator URI określony przez `--channelUri` (która musi być określona gdy `--installChannelUri` określono) jest używana do wykrywania aktualizacji. Może być używany dla polecenia install; jest on ignorowany dla innych poleceń. |
| `--installCatalogUri <uri>` | **Opcjonalne**: identyfikator URI manifestu katalogu do użycia podczas instalacji. Jeśli zostanie określona, Menedżer kanałów prób pobrania manifest katalogu z tego identyfikatora URI przed rozpoczęciem korzystania z identyfikatora URI w manifeście kanału instalacji. Ten parametr jest używany do obsługi instalacji w trybie offline, w której zostanie utworzony układ pamięci podręcznej z katalogu produktów już pobrane. Może być używany dla polecenia install; jest on ignorowany dla innych poleceń. |
| `--productId <id>` | **Opcjonalne** identyfikator produktu dla tego wystąpienia, który zostanie zainstalowany. To jest wypełniana wstępnie w warunkach normalnej instalacji. |
| `--wait` | **Opcjonalne**: proces będzie zaczekać na ukończenie instalacji przed zwróceniem kod zakończenia. Jest to przydatne, gdy zainstalować automatyzacji instalacji, gdzie należy poczekać na zakończenie obsługi kod powrotny od tej instalacji. |
| `--locale <language-locale>` | **Opcjonalne**: Zmienianie języka wyświetlania interfejsu użytkownika samego Instalatora. Ustawienia zostaną utrwalone. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--cache` | **Nowość w 15,2 opcjonalne**: Jeśli jest obecny, pakiety zostaną zachowane po zainstalowaniu dla kolejnych naprawy. Przesłania globalne ustawienia do zastosowania w przypadku kolejnych instaluje, naprawia lub zmiany zasad. Domyślna zasada jest pakiety w pamięci podręcznej. To jest ignorowany dla polecenia dezinstalacji. Jak do odczytu do [wyłączone lub Przenieś pamięć podręczną pakietów](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--nocache` | **Nowość w 15,2 opcjonalne**: Jeśli jest obecny, pakiety zostaną usunięte po zainstalować lub naprawić. Tylko wtedy, gdy są potrzebne i usuwane ponownie po użyciu będzie można ponownie pobrać. Przesłania globalne ustawienia do zastosowania w przypadku kolejnych instaluje, naprawia lub zmiany zasad. Domyślna zasada jest pakiety w pamięci podręcznej. To jest ignorowany dla polecenia dezinstalacji. Jak do odczytu do [wyłączone lub Przenieś pamięć podręczną pakietów](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--noUpdateInstaller` | **Nowość w 15,2 opcjonalne**: Jeśli jest obecny, Instalatorowi na aktualizowanie się, gdy określono cichy. Instalator niepowodzenie polecenia i zwraca kod zakończenia inną niż zero, jeśli noUpdateInstaller zostanie określony z okna, gdy wymagana jest aktualizacja Instalatora. |
| `--noWeb` | **Nowość w 15 ustęp 3, opcjonalnie**: Instalator pobierze teraz żadnej zawartości, który jest instalowany z Internetu.  Cała zawartość, który jest instalowany musi być dostępny w układzie w trybie offline.  Układu nie ma zawartości, instalacja zakończy się niepowodzeniem.  Aby uzyskać więcej informacji, zobacz [wdrażania z instalacji sieciowej](create-a-network-installation-of-visual-studio.md). |
| `--path <name>=<path>` | **Nowość w 15.7 opcjonalne**: służy do określania ścieżki instalacji niestandardowej instalacji. Obsługiwana ścieżka, których nazwy są udostępniane, pamięci podręcznej i instalacji. |
| `--path cache=<path>` | **Nowość w 15.7 opcjonalne**: używa lokalizacji określ pobierania plików instalacyjnych. Tej lokalizacji można ustawić tylko po raz pierwszy jest zainstalowany program Visual Studio. Przykład: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Nowość w 15.7 opcjonalne**: zawiera pliki udostępnione do instalacji programu Visual Studio side-by-side. Niektóre narzędzia i zestawy SDK zainstalować produkt w lokalizacji na dysku, podczas gdy inne mogą zastąpić to ustawienie, zainstaluj na inny dysk. Przykład: `--path shared="C:\VS\shared"` <br><br>Ważne: To można ustawić tylko raz i zainstalowaniu programu Visual Studio po raz pierwszy. |
| `--path install=<path>` | **Nowość w 15.7 opcjonalne**: odpowiednikiem `–-installPath`. W szczególności `--installPath "C:\VS"` i `--path install="C:\VS"` są równoważne. Jednocześnie można użyć tylko jeden z tych. |

## <a name="list-of-workload-ids-and-component-ids"></a>Lista identyfikatorów obciążenia i identyfikatory składników

Listę obciążenia i identyfikatory składników posortowane według produktu Visual Studio, zobacz [obciążenia 2017 r w usłudze Visual Studio i identyfikatory składników](workload-and-component-ids.md) strony.

## <a name="list-of-language-locales"></a>Lista ustawień regionalnych języka

| **Ustawienia regionalne języka** | **Język** |
| ----------------------- | --------------- |
| CS-cz | czeski |
| De-de | niemiecki |
| en-us | Angielski |
| Es-es | Hiszpański |
| Fr-fr | Francuski |
| IT-it | Włoski |
| Ja-jp | japoński |
| Ko-kr | koreański |
| Pl-pl | polski |
| Pt-br | Portugalski (Brazylia) |
| Ru-ru | Rosyjski |
| TR-tr | turecki |
| Zh-cn | Chiński (uproszczony) |
| Zh-tw. | Chiński — tradycyjny |

## <a name="error-codes"></a>Kody błędów

W zależności od wyniku operacji `%ERRORLEVEL%` zmienna środowiskowa jest ustawiona na jedną z następujących wartości:

| **Wartość** | **wynik** |
| --------- | ---------- |
| 0 | Operacja została wykonana pomyślnie |
| 1602 | Operacja została anulowana |
| 3010 | Operacja zakończyła się pomyślnie, ale instalacja wymaga ponownego uruchomienia, zanim będzie można go używać. |
| 5004 | Operacja została anulowana |
| 5007 | Operacja została zablokowana - komputer nie spełnia wymagań |
| Inne | Wystąpił błąd warunku — Sprawdź dzienniki, aby uzyskać więcej informacji |

Każda operacja generuje kilka plików dziennika w `%TEMP%` katalogu, który wskazuje postęp instalacji. Sortowanie folderu według daty i wyszukaj pliki, które zaczynają się od `dd_bootstrapper`, `dd_client`, i `dd_setup` dla programu inicjującego, Instalator aplikacji i ustawień aparatu, odpowiednio.

## <a name="get-support"></a>Uzyskaj pomoc techniczną

Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu i odpowiedzi w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/).
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio). (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Przykłady parametru wiersza polecenia do instalacji programu Visual Studio 2017 r.](command-line-parameter-examples.md)
* [Tworzenie w trybie offline instalację programu Visual Studio 2017 r.](create-an-offline-installation-of-visual-studio.md)
* [Zautomatyzowana instalacja programu Visual Studio przy użyciu pliku odpowiedzi](automated-installation-with-response-file.md)
