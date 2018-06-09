---
title: Samouczek narzędzia Kubernetes | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/08/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- azure
ms.openlocfilehash: a2bdc24a3e1ee30ffa569fa0c9e5b2ab208aa7ef
ms.sourcegitcommit: 886759fb35a88f6ef5452c5b2e33a1f71da4489a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "34851893"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Wprowadzenie do programu Visual Studio Tools Kubernetes

Visual Studio Kubernetes Tools usprawnić tworzenie konteneryzowanych aplikacji przeznaczonych dla Kubernetes. Visual Studio może automatycznie tworzyć wymagane do obsługi wdrożenia Kubernetes, takich jak wykresy Dockerfiles i Helm pliki konfiguracji jako kod. Ponadto można publikować bezpośrednio do klastra usługi Kubernetes Azure (AKS) programu Visual Studio.

## <a name="prerequisites"></a>Wymagania wstępne

Aby korzystać z tej nowej funkcji, musisz:

- W najnowszej wersji zapoznawczej [programu Visual Studio 2017](https://www.visualstudio.com/vs/preview) z obciążeniem rozwoju platformy Azure.

- [Kubernetes narzędzi dla programu Visual Studio](https://aka.ms/get-vsk8stools), dostępne jako osobny plik do pobrania.

- [Docker dla systemu Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows) zainstalowane na deweloperskiej stacji roboczej (oznacza to, gdzie należy uruchomić program Visual Studio)

- Jeśli chcesz opublikować AKS z programu Visual Studio:

    1.  [AKS narzędzia publikowania](https://aka.ms/get-vsk8spublish), dostępne jako osobny plik do pobrania.

    1.  Kubernetes klastra usługi platformy Azure. Aby uzyskać więcej informacji, zobacz [tworzenia klastra AKS](/azure/aks/kubernetes-walkthrough-portal#create-aks-cluster). Upewnij się, [Połącz się z klastrem](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) z deweloperskiej stacji roboczej.

    1.  Helm CLI zainstalowane na deweloperskiej stacji roboczej. Aby uzyskać więcej informacji, zobacz [instalowanie Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1.  Helm skonfigurowana przed AKS klastra. Aby uzyskać więcej informacji, jak to zrobić, zobacz [Konfigurowanie Helm](/azure/aks/kubernetes-helm#configure-helm).

## <a name="create-a-new-kubernetes-project"></a>Utwórz nowy projekt Kubernetes

Po utworzeniu odpowiednich narzędzi, które są zainstalowane, uruchom program Visual Studio i utworzyć nowy projekt. W obszarze **chmury**, wybierz **aplikacji kontenera dla Kubernetes** typu projektu. Wybierz ten typ projektu i wybierz polecenie **OK**.

![Zrzut ekranu przedstawiający tworzenie nowego projektu aplikacji Kubernetes](media/k8s-tools-new-k8s-app.png)

Następnie możesz typu platformy ASP.NET Core aplikacji sieci web do utworzenia. Wybierz **aplikacji sieci Web** i wybierz polecenie **OK**. Zwykle **Włącz obsługę Docker** opcja nie jest widoczna w tym oknie dialogowym.  Obsługa docker jest domyślnie włączona dla aplikacji kontenera dla Kubernetes.

![Zrzut ekranu przedstawiający wybór aplikacji sieci web](media/k8s-tools-web-app-selection-screen.png)

## <a name="add-kubernetes-support-to-an-existing-project"></a>Dodaj obsługę Kubernetes do istniejącego projektu

Alternatywnie można dodać obsługę Kubernetes do istniejącego projektu aplikacji sieci web platformy ASP.NET Core. Aby to zrobić, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **Obsługa Orchestrator kontenerów**.

![Zrzut ekranu z dodać kontener Orchestrator elementu menu](media/k8s-tools-add-container-orchestrator.png)

W oknie dialogowym zaznacz "Kubernetes/Helm" i wybierz polecenie **OK**.

![Zrzut ekranu z dodać kontener Orchestrator — okno dialogowe](media/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Program Visual Studio tworzy dla Ciebie

Po utworzeniu nowego **aplikacji kontenera dla Kubernetes** projektu lub dodanie obsługi orchestrator kontenera Kubernetes do istniejącego projektu, zobacz niektóre dodatkowe pliki w projekcie, które ułatwiają wdrażanie Kubernetes.

![Zrzut ekranu Eksploratora rozwiązań po dodaniu obsługi kontenera programu Orchestrator](media/k8s-tools-solution-explorer.png)

Dodano pliki są:

- Plik Dockerfile, dzięki czemu można wygenerować Docker obrazu kontenera hostującej tę aplikację sieci web. Jak można zauważyć, narzędzia programu Visual Studio wykorzystuje ten plik Dockerfile podczas debugowania i wdrażania Kubernetes. Jeśli wolisz pracować bezpośrednio z obrazu Docker można kliknij prawym przyciskiem myszy plik Dockerfile i wybrać **kompilacji obrazu Docker**.

   ![Zrzut ekranu z kompilacji Docker opcja obraz](media/k8s-tools-build-docker-image.png)

- Wykres Helm i *wykresów* folderu. Te pliki yaml programu składają się na wykresie Helm dla aplikacji, w którym można wdrożyć w Kubernetes. Aby uzyskać więcej informacji o Helm, zobacz [ https://www.helm.sh ](https://www.helm.sh).

- *azds.yaml*. Zawiera ustawienia Azure deweloperów spacji, nową usługę, która zapewnia szybkie, iteracji debugowania w usłudze Azure Kubernetes Service. Ten plik jest aktualnie używana, ale jest zarezerwowany do użytku w przyszłości spacjami deweloperów platformy Azure.

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publikowanie do usługi Azure Kubernetes (AKS)

Wszystkie te pliki w miejscu służy środowiska IDE programu Visual Studio do zapisu i debugowanie kodu aplikacji, tak samo, jak zawsze mieć.

Po utworzeniu kodu z oczekiwaniami, można opublikować bezpośrednio z programu Visual Studio AKS klastra.

Aby to zrobić, należy najpierw skonfigurować profil publikowania, który publikuje obrazu kontenera do rejestru kontenera platformy Azure (ACR). Następnie AKS można ściąganie kontener obrazu z ACR i wdrożyć go do klastra.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy użytkownika *projektu* i wybierz polecenie **publikowania**.

   ![Zrzut ekranu opublikować element menu](media/k8s-tools-publish-project.png)

1. W **publikowania** ekranu, wybierz **rejestru kontenera** jako publikowanie docelowego i postępuj zgodnie z monitami, aby wybrać rejestru kontenera. Jeśli nie masz jeszcze rejestru kontenera, wybierz **tworzenie nowych rejestru kontenera Azure** go utworzyć za pomocą programu Visual Studio. Aby uzyskać więcej informacji, zobacz [publikowania z kontenera do rejestru kontenera Azure](#publish-your-container-to-azure-container-registry).

   ![Zrzut ekranu przedstawiający pobrania ekranu docelowej publikowania](media/k8s-tools-publish-to-acr.png)

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy użytkownika *rozwiązania* i kliknij przycisk **publikowanie Azure AKS**.

   ![Zrzut ekranu z opublikować element menu Azure AKS](media/k8s-tools-publish-solution.png)

1. Wybierz subskrypcję, a klaster AKS, wraz z ACR publikowanie profil, który został właśnie utworzony. Następnie kliknij przycisk **OK**.

   ![Zrzut ekranu z publikowania AKS ekranu](media/k8s-tools-publish-to-aks.png)

   Powoduje to przejście do **publikowanie Azure AKS** ekranu.

1.  Wybierz **skonfigurować Helm** łącze, aby zaktualizować wiersza polecenia używane do instalowania wykresy Helm na serwerze.

   ![Zrzut ekranu skonfigurować Helm łącza](media/k8s-tools-configure-helm.png)

   Aktualizacja wiersza polecenia jest przydatna, jeśli istnieją argumenty wiersza polecenia niestandardowych, które chcesz określić, takich jak inną nazwę kontekstu lub wykres Kubernetes.

   ![Screenshoot Helm skonfigurować ekranu](media/k8s-tools-helm-configure-screen.png)

1. Gdy wszystko będzie gotowe do wdrożenia, kliknij przycisk **publikowania** przycisk, aby opublikować aplikację do AKS.

   ![Zrzut ekranu przedstawiający publikowanie do ekranu Azure AKS](media/k8s-tools-publish-screen.png)

Gratulacje! Można teraz używać pełnych możliwości programu Visual Studio dla wszystkich tworzenia aplikacji Kubernetes.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o programowanie Kubernetes na platformie Azure, odczytując [dokumentacji AKS](/azure/aks).