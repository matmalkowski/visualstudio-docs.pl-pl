---
title: Samouczka dotyczącego narzędzia Kubernetes | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/08/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- azure
ms.openlocfilehash: f842d1f9c103e9673d3295b2b285498d6ff58045
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138946"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Rozpoczynanie pracy z usługą Visual Studio Tools rozwiązania Kubernetes

Visual Studio Kubernetes Tools usprawnić tworzenie konteneryzowanych aplikacji przeznaczonych dla platformy Kubernetes. Program Visual Studio może automatycznie tworzyć pliki konfiguracji jako kodu, potrzebne do obsługi platformy Kubernetes, takiego jak wdrożenie plików Dockerfile i Helm wykresów. Debugowanie kodu na żywo za pomocą usługi Azure Dev miejsca do magazynowania klastra Azure Kubernetes Service (AKS) lub opublikować bezpośrednio do klastra usługi AKS z poziomu programu Visual Studio.

## <a name="prerequisites"></a>Wymagania wstępne

Aby korzystać z tej nowej funkcji, należy:

- Najnowszą wersję [programu Visual Studio 2017](https://visualstudio.microsoft.com/download) z *ASP.NET i tworzenie aplikacji internetowych* obciążenia.

- [Narzędzi usługi Kubernetes dla programu Visual Studio](https://aka.ms/get-vsk8stools), która jest dostępna do pobrania osobno.

- [Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows) zainstalowane na deweloperskiej stacji roboczej (oznacza to, gdzie możesz uruchomić program Visual Studio), jeśli chcesz skompilować obrazy Docker, debugowanie kontenerów platformy Docker działa lokalnie, lub opublikować w usłudze AKS.

- Jeśli chcesz opublikować w usłudze AKS za pomocą programu Visual Studio:

    1.  [AKS narzędzia publikowania](https://aka.ms/get-vsk8spublish), która jest dostępna do pobrania osobno.

    1.  Klaster Azure Kubernetes Service. Aby uzyskać więcej informacji, zobacz [tworzenia klastra usługi AKS](/azure/aks/kubernetes-walkthrough-portal#create-aks-cluster). Pamiętaj, aby [łączenia z klastrem](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) z deweloperskiej stacji roboczej.

    1.  Polecenie Helm interfejsu wiersza polecenia, zainstalowane na deweloperskiej stacji roboczej. Aby uzyskać więcej informacji, zobacz [instalowanie narzędzia Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1.  Polecenie Helm skonfigurowane dla klastra usługi AKS. Aby uzyskać więcej informacji na temat jak to zrobić, zobacz [sposobu konfigurowania Helm](/azure/aks/kubernetes-helm#configure-helm).

## <a name="create-a-new-kubernetes-project"></a>Utwórz nowy projekt rozwiązania Kubernetes

Po utworzeniu odpowiednich narzędzi, które są zainstalowane, uruchom program Visual Studio i Utwórz nowy projekt. W obszarze **chmury**, wybierz **aplikacji kontenera dla rozwiązania Kubernetes** typ projektu. Wybierz ten typ projektu, a następnie wybierz **OK**.

![Zrzut ekranu przedstawiający tworzenie nowego projektu aplikacji platformy Kubernetes](media/k8s-tools-new-k8s-app.png)

Można następnie jakiego typu platforma ASP.NET Core w aplikacji sieci web do utworzenia. Wybierz **aplikacji sieci Web** i wybierz polecenie **OK**. Zwykle **włączyć obsługę platformy Docker** opcja nie jest wyświetlana w tym oknie dialogowym.  Obsługę platformy docker jest domyślnie włączone dla aplikacji kontenera dla rozwiązania Kubernetes.

![Zrzut ekranu przedstawiający wybór aplikacji sieci web](media/k8s-tools-web-app-selection-screen.png)

## <a name="add-kubernetes-support-to-an-existing-project"></a>Dodawanie Obsługa klastra Kubernetes do istniejącego projektu

Alternatywnie można dodać Obsługa klastra Kubernetes do istniejącego projektu aplikacji sieci web platformy ASP.NET Core. Aby to zrobić, kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie **Dodaj** > **obsługi Orkiestratora kontenerów**.

![Zrzut ekranu z Dodaj koordynatorem kontenera elementu menu.](media/k8s-tools-add-container-orchestrator.png)

W oknie dialogowym wybierz opcję "Kubernetes/Helm", a następnie wybierz **OK**.

![Zrzut ekranu z Dodaj Orkiestrator kontenerów, okno dialogowe](media/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Program Visual Studio utworzy dla Ciebie

Po utworzeniu nowego **aplikacji kontenera dla rozwiązania Kubernetes** projektu lub dodawania obsługi orkiestratora kontenera Kubernetes do istniejącego projektu, zobaczysz niektóre dodatkowe pliki w projekcie, które ułatwiają wdrażanie platformy Kubernetes.

![Zrzut ekranu Eksploratora rozwiązań po dodaniu obsługi Orkiestratora kontenerów](media/k8s-tools-solution-explorer.png)

Dodano pliki są:

- Plik Dockerfile, który umożliwia generowanie Docker obrazów kontenera hostowania tej aplikacji sieci web. Jak można zauważyć, narzędzia programu Visual Studio korzysta z tego pliku Dockerfile podczas debugowania i wdrażania w usłudze Kubernetes. Jeśli wolisz pracować bezpośrednio z obrazu platformy Docker, możesz kliknąć prawym przyciskiem myszy w pliku Dockerfile i wybrać **tworzenia obrazu platformy Docker**.

   ![Zrzut ekranu z tworzenia obrazu platformy Docker — opcja](media/k8s-tools-build-docker-image.png)

- Wykres Helm i *wykresy* folderu. Te pliki yaml tworzą wykresu Helm w aplikacji, w którym można wdrożyć w usłudze Kubernetes. Aby uzyskać więcej informacji na temat narzędzia Helm, zobacz [ https://www.helm.sh ](https://www.helm.sh).

- *azds.yaml*. Zawiera ustawienia dla usługi Azure Dev spacje, co zapewnia szybkie, iteracyjne środowiska debugowania w usłudze Azure Kubernetes Service. Aby uzyskać więcej informacji, zobacz [dokumentacji usługi Azure Dev miejsca do magazynowania](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces).

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publikowanie w usłudze Azure Kubernetes Service (AKS)

Wszystkie te pliki w miejscu można użyć środowiska IDE programu Visual Studio umożliwia pisanie i debugowanie kodu aplikacji, tak samo, jak zawsze mieć.

Po utworzeniu działanie kodu tak jak chcesz, możesz opublikować bezpośrednio z programu Visual Studio klastra usługi AKS.

Aby to zrobić, należy najpierw skonfigurować profil publikowania, który publikuje obraz kontenera do usługi Azure Container Registry (ACR). Następnie AKS można ściągnąć obraz kontenera z rejestru Azure container Registry i wdrożenia go w klastrze.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy użytkownika *projektu* i wybierz polecenie **Publikuj**.

   ![Zrzut ekranu opublikować element menu](media/k8s-tools-publish-project.png)

1. W **Publikuj** ekranu, wybierz **Container Registry** jako publikowania docelowy, a następnie postępuj zgodnie z monitami, aby wybrać usługi container registry. Jeśli nie masz jeszcze rejestru kontenerów, wybierz opcję **Tworzenie nowej usługi Azure Container Registry** ją utworzyć za pomocą programu Visual Studio. Aby uzyskać więcej informacji, zobacz [opublikowany kontener w usłudze Azure Container Registry](#publish-your-container-to-azure-container-registry).

   ![Zrzut ekranu przedstawiający wybierz ekran docelowy publikowania](media/k8s-tools-publish-to-acr.png)

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy użytkownika *rozwiązania* i kliknij przycisk **publikowanie w usłudze Azure AKS**.

   ![Zrzut ekranu z opublikować element menu platformy Azure w usłudze AKS](media/k8s-tools-publish-solution.png)

1. Wybierz subskrypcję i klastra usługi AKS, wraz z rekordu ACR opublikować profil, który został utworzony. Następnie kliknij przycisk **OK**.

   ![Zrzut ekranu z publikowania do ekranu usługi AKS](media/k8s-tools-publish-to-aks.png)

   Spowoduje to przejście do **publikowanie w usłudze Azure AKS** ekranu.

1.  Wybierz **skonfigurować Helm** łącze, aby zaktualizować wiersza polecenia używane do instalowania wykresów rozwiązania Helm na serwerze.

   ![Zrzut ekranu z skonfigurować narzędzia Helm łącza](media/k8s-tools-configure-helm.png)

   Aktualizowanie wiersza polecenia jest przydatne, jeśli argumenty niestandardowe wiersza polecenia, które chcesz określić, takich jak Kubernetes kontekstu lub wykresu innej.

   ![Zrzut ekranu narzędzia Helm, skonfigurować ekran](media/k8s-tools-helm-configure-screen.png)

1. Gdy wszystko jest gotowe do wdrożenia, kliknij przycisk **Publikuj** przycisk, aby opublikować aplikację w usłudze AKS.

   ![Zrzut ekranu przedstawiający publikowanie do usługi Azure AKS ekranu](media/k8s-tools-publish-screen.png)

Gratulacje! Można teraz używać pełnych możliwości programu Visual Studio wszystkie tworzenia aplikacji platformy Kubernetes.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat programowania w usłudze Kubernetes na platformie Azure, czytając [dokumentację dotyczącą usługi AKS](/azure/aks).
