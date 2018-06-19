---
title: 'Utwórz Środowisko deweloperskie .NET Core z kontenerów przy użyciu Kubernetes w chmurze za pomocą programu Visual Studio: krok 3: Utwórz Środowisko deweloperskie Kubernetes | Dokumentacja firmy Microsoft'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: douge
ms.openlocfilehash: 6226340b1744e95bbb375d47213ae00bb9e76565
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31884388"
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Rozpoczynanie pracy w środowisku połączonych z platformy .NET Core i Visual Studio

Poprzedni krok: [tworzenia aplikacji sieci web ASP.NET](get-started-netcore-visualstudio-02.md)

## <a name="create-a-dev-environment-in-azure"></a>Tworzenie środowiska deweloperskiego na platformie Azure
W środowiskach połączone można utworzyć środowiska programowania opartego na Kubernetes, które są w pełni zarządzane przez usługę Azure i zoptymalizowane pod kątem tworzenia. W projekcie właśnie utworzyliśmy Otwórz wybierz **połączone środowisko AKS** z rozwijanej Ustawienia uruchamiania, jak pokazano poniżej.

![](images/LaunchSettings.png)

W oknie dialogowym, który jest wyświetlany obok upewnij się, że logujesz się przy użyciu odpowiedniego konta, a następnie wybierz istniejące środowisko deweloperskie, lub wybierz **< Utwórz nowy połączony środowisko dla AKS... >** Aby utworzyć nowy.

![](images/ConnectedEnvDialog.png)

Można użyć wartości domyślnych lub Dostosuj je, według uznania. Kliknij przycisk **OK** gdy wartości zostały ustawione prawidłowo.

![](images/NewEnvDialog.png)

Do poprzedniego okna dialogowego pozostaw **miejsca** listy rozwijanej domyślnie `mainline` teraz omówimy to później bardziej szczegółowo. Sprawdź **publicznie** pole wyboru, aplikacji sieci web będzie dostępny za pośrednictwem publicznego punktu końcowego. Nie jest to wymagane, ale będą pomocne zademonstrować dotyczące pojęć w dalszej części tego przewodnika. Ale nie martw się, w obu przypadkach można debugować witryny sieci Web przy użyciu programu Visual Studio.

![](images/ConnectedEnvDialog2.png)

Kliknij przycisk **OK** aby wybrać lub utworzyć środowisko deweloperskie. Zadanie w tle zostanie uruchomione w tym celu, potrwa liczbę minut. Widać, jeśli jest on nadal jest tworzony, ustawiając kursor kursor nad **zadania w tle** ikonę w lewym dolnym rogu stan paska (patrz poniżej).

![](images/BackgroundTasks.png)

> [!Note]
Dopóki środowisko projektowe został utworzony pomyślnie, nie można debugować aplikacji.

## <a name="look-at-the-files-added-to-project"></a>Przyjrzyj się pliki dodane do projektu
Podczas oczekiwania na środowisko deweloperskie do utworzenia, Przyjrzyjmy się pliki, które zostały dodane do projektu, gdy wybrano używanie Środowisko deweloperskie.

Najpierw mogą widzieć folder o nazwie `charts` został dodany, a w ramach tego [wykresu Helm](https://docs.helm.sh) dla Tworzenie szkieletu aplikacji. Te pliki służą do wdrażania aplikacji w środowisku programistycznym.

Zobaczysz plik o nazwie `Dockerfile` został dodany. Ten plik zawiera informacje potrzebne do pakietu aplikacji w standardowym formacie Docker. A `HeaderPropagation.cs` jest też tworzony plik, omówimy tego pliku w dalszej części przewodnika. 

Ponadto zobaczysz plik o nazwie `vsce.yaml` zawierającą informacje o konfiguracji, które są wymagane przez środowisko deweloperskie, takie jak określa, czy aplikacja powinna być dostępny za pośrednictwem publicznego punktu końcowego.

![](images/ProjectFiles.png)

> [!div class="nextstepaction"]
> [Debugowanie kontenera w Kubernetes](get-started-netcore-visualstudio-04.md)