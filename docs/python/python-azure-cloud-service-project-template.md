---
title: Szablon projektu usługi chmury Azure dla języka Python
description: Przegląd szablonu Visual Studio dla usług w chmurze Azure napisanych w języku Python w tym wdrażanie ról w zależności i rozwiązywania problemów.
ms.date: 07/13/2017
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 42b2cf1fda241e178804847d86e6af9e4f33e7bd
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="azure-cloud-service-projects-for-python"></a>Projekty usługi w chmurze Azure dla języka Python

Visual Studio zawiera szablony ułatwiające rozpoczęcie pracy tworzenia usługi w chmurze Azure przy użyciu języka Python.

A [usługi w chmurze](https://docs.microsoft.com/azure/cloud-services/) składa się z dowolnej liczby *roli proces roboczy* i *sieci web ról*, z których każdy wykonuje koncepcyjnie osobnym zadaniem, ale można osobno być replikowane na maszyny wirtualne w razie potrzeby skalowania. Role sieci Web zawierają hosting aplikacji frontonu sieci web. W przypadku danego języka Python, wszelkie platforma sieci web, który obsługuje WSGI może służyć do pisania takich aplikacji (obsługiwana przez [szablonu projektu sieci Web](python-web-application-project-templates.md)). Proces roboczy są przeznaczone dla procesy długotrwałe, które nie bezpośrednią interakcję z użytkownikami. Zwykle należy używać pakietów w pakiecie "azure", który jest instalowany z [ `pip install azure` ](http://pypi.org/project/azure).

Ten artykuł zawiera szczegółowe informacje o szablonie projektu i innych pomoc techniczna w Visual Studio 2017 r (wcześniejszych wersji są podobne, lecz w edytorze). Aby uzyskać więcej informacji na temat pracy z platformą Azure w języku Python, odwiedź [Centrum deweloperów języka Python Azure](https://docs.microsoft.com/en-us/python/azure/?view=azure-python).

## <a name="create-a-project"></a>Tworzenie projektu

1. Zainstaluj [zestawu Azure SDK .NET dla programu Visual Studio](https://www.visualstudio.com/vs/azure-tools/), które jest wymagane do używania szablonu usługi w chmurze.
1. W programie Visual Studio, wybierz **Plik > Nowy > Projekt...** , następnie wyszukaj "Azure Python" i wybierz **usługi w chmurze Azure** z listy:

    ![Szablonu projektu w chmurze Azure dla języka Python](media/template-azure-cloud-project.png)

1. Wybierz co najmniej jedną rolę do uwzględnienia. Projekty chmury mogą łączyć role zapisywane w różnych językach, dzięki czemu można łatwo zapisu każdej części aplikacji w najbardziej odpowiedniego języka. Aby dodać nowe role do projektu po zakończeniu tego okna dialogowego, kliknij prawym przyciskiem myszy **ról** w Eksploratorze rozwiązań i wybierz jedną z pozycji w obszarze **Dodaj**.

    ![Dodawanie ról w szablonie projektu w chmurze Azure](media/template-azure-cloud-service-project-wizard.png)

1. Podczas tworzenia projektów poszczególnych ról, a monit może zainstalować dodatkowe pakiety Python, takie jak struktury Django i Bottle, Flask, w przypadku wybrania roli, która korzysta z jednego z tych.

1. Po dodaniu nowej roli do projektu, są wyświetlane instrukcje konfiguracji. Zmiany w konfiguracji nie są zazwyczaj konieczne, ale mogą być przydatne do dostosowywania przyszłych projektów. Należy pamiętać, że podczas dodawania wielu ról w tym samym czasie, pozostają otwarte, tylko instrukcje dotyczące ostatniego roli. Jednak można znaleźć instrukcje i wskazówki dotyczące rozwiązywania problemów dla innych ról w odpowiednich `readme.mht` plików znajdujących się w katalogu głównym roli lub w `bin` folderu.

1. Projekt `bin` folder zawiera także jednego lub dwóch skryptów programu PowerShell, które są używane do konfigurowania zdalnego maszyny wirtualnej, w tym wszelkie instalacji języka Python, [requirements.txt](#dependencies) pliku w projekcie i konfigurowania usług IIS, jeśli niezbędne. Można edytować te pliki do wdrożenia, chociaż można zarządzać w inny sposób najczęściej używanych opcji (zobacz [Konfigurowanie wdrażania roli](#configuring-role-deployment) poniżej). Nie zaleca się usunięcie tych plików, ponieważ skrypt konfiguracji starszych zamiast niego jest używana, jeśli pliki nie są dostępne.

    ![Pliki obsługi roli procesu roboczego](media/template-azure-cloud-service-worker-role-support-files.png)

    Aby dodać te skrypty do konfiguracji do nowego projektu, kliknij prawym przyciskiem myszy projekt, wybierz **Dodaj > Nowy element...** i wybierz opcję **pliki obsługi roli sieci Web** lub **pliki obsługi roli procesu roboczego**.

## <a name="configuring-role-deployment"></a>Konfigurowanie wdrażania roli

Skrypty programu PowerShell w projekcie roli `bin` folderu kontroli wdrożenia tej roli i może być edytowana do dostosowywania konfiguracji:

- `ConfigureCloudService.ps1` Służy do ról sieć web i proces roboczy, zwykle można zainstalować i skonfigurować zależności i ustaw wersję języka Python.
- `LaunchWorker.ps1` jest używany tylko dla roli proces roboczy i umożliwia zmianę zachowania podczas uruchamiania, Dodaj argumenty wiersza polecenia lub dodać zmienne środowiskowe.

Oba pliki zawierają instrukcje dotyczące dostosowywania. Można także zainstalować wersji środowiska Python, dodając inne zadanie do projektu usługi chmury głównego `ServiceDefinition.csdef` pliku z ustawieniami `PYTHON` zmienną do jego zainstalowanych `python.exe` (lub równoważnego) ścieżki. Gdy `PYTHON` jest ustawiona, Python nie jest zainstalowana z NuGet.

Dodatkowe czynności konfiguracyjne można zrobić w następujący sposób:

1. Zainstaluj pakiety przy użyciu `pip` , aktualizując `requirements.txt` pliku w katalogu głównym projektu. `ConfigureCloudService.ps1` Skryptu instaluje ten plik na wdrożenie.
1. Ustaw zmienne środowiskowe, modyfikując Twojej `web.config` pliku (role sieci web) lub `Runtime` części Twojego `ServiceDefinition.csdef` pliku (roli proces roboczy).
1. Określ skrypt i argumenty do użycia dla roli proces roboczy, modyfikując wiersza polecenia w `Runtime/EntryPoint` części Twojego `ServiceDefinitions.csdef` pliku.
1. Ustaw skryptu głównym programu obsługi dla roli sieci web za pośrednictwem `web.config` pliku.

## <a name="testing-role-deployment"></a>Testowanie wdrażania roli

Podczas zapisywania ról, można przetestować projekt chmury lokalnie przy użyciu emulatora usługi w chmurze. Emulator jest dołączana do pakietu Azure SDK Tools i ograniczoną wersję środowiska używane po opublikowaniu usługi w chmurze na platformie Azure.

Uruchom emulator, najpierw upewnij się projektu w chmurze jest projekt startowy w rozwiązaniu prawym przyciskiem myszy i wybierając **Ustaw jako projekt startowy**. Następnie wybierz **Debuguj > Rozpocznij debugowanie** (F5) lub **debugowania > Uruchom bez debugowania** (Ctrl + F5).

Należy pamiętać, że z powodu ograniczeń w emulatorze nie jest możliwe do debugowania kodu języka Python. Dlatego zalecamy debugować role przez uruchomienie ich niezależnie, a następnie użyć emulatora do integracji testowania przed opublikowaniem.

## <a name="deploying-a-role"></a>Wdrażanie roli

Aby otworzyć **publikowania** kreatora, wybierz rolę projekt w Eksploratorze rozwiązań i wybierz **kompilacji > Publikuj** z menu głównego, lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania**.

Proces publikowania wiąże się z dwóch faz. Po pierwsze Visual Studio tworzy pojedynczy pakiet zawierający wszystkie role dla usługi w chmurze. Ten pakiet jest, co jest wdrożony na platformie Azure, która inicjuje co najmniej jednej maszyny wirtualnej dla każdej roli i wdrożyć źródła.

Ponieważ każda maszyna wirtualna zostanie aktywowany, wykonuje `ConfigureCloudService.ps1` skryptów i zainstaluj zależności. Ten skrypt domyślnie instaluje najnowszą wersję języka Python z [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) i ewentualnych pakietów, określona w `requirements.txt` pliku.

Następnie uruchom proces roboczy `LaunchWorker.ps1`, którego uruchomienie skryptu języka Python; sieci web zainicjować ról usług IIS i rozpocząć obsługę żądań sieci web.

## <a name="dependencies"></a>Zależności

Dla usług w chmurze `ConfigureCloudService.ps1` skrypt używa `pip` zainstalować zestaw Python zależności. Zależności powinny być określone w pliku o nazwie `requirements.txt` (można dostosować, modyfikując `ConfigureCloudService.ps1`). Plik jest wykonywany z `pip install -r requirements.txt` jako część inicjowania.

Należy pamiętać, że wystąpienia usługi chmury nie zawierają kompilatory C, dlatego wszystkie biblioteki z rozszerzeniami C podać wstępnie skompilowanych plików binarnych.

PIP i jego zależności, a także pakietów w `requirements.txt`, są automatycznie pobierane i może być liczona jako mogą być obciążane przepustowości. Zobacz [zarządzania wymagane pakiety](managing-required-packages-with-requirements-txt.md) szczegółowe informacje na temat zarządzania `requirements.txt` plików.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli po wdrożeniu roli użytkownika sieci web lub procesu roboczego nie zadziała poprawnie, sprawdź następujące informacje:

- Projekt Python zawiera folder bin\ o (co najmniej):

  - `ConfigureCloudService.ps1`
  - `LaunchWorker.ps1` (dla ról procesów roboczych)
  - `ps.cmd`

- Projekt Python zawiera `requirements.txt` pliku wyświetlanie listy wszystkich zależności (lub alternatywnie Kolekcja plików koło).
- Włączenie pulpitu zdalnego na usługi w chmurze i sprawdź pliki dziennika.
- W dziennikach `ConfigureCloudService.ps1` i `LaunchWorker.ps1` są przechowywane w `C:\Resources\Directory\%RoleId%.DiagnosticStore\LogFiles` folderu na komputerze zdalnym.
- Role sieci Web może tworzyć dodatkowe dzienniki ścieżki skonfigurowane w `web.config`, czyli ścieżki `WSGI_LOG` appSetting. Działa także najbardziej regularne rejestrowanie usług IIS i FastCGI.
- Obecnie `LaunchWorker.ps1.log` plik jest jedynym sposobem, aby wyświetlić dane wyjściowe lub błędy wyświetlane przez rolę proces roboczy języka Python.