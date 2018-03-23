---
title: Jak używać kubectl środowiska połączone z | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 03/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: 46c69f80e58a4265aa5e4320e731c3ad241a8116
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="use-kubectl-with-a-connected-environment"></a>Użyj `kubectl` o środowisku połączonym

Mają dostęp klastra Kubernetes w środowisku podłączony, i użyj istniejącego Kubernetes narzędzi, takich jak `kubectl`.

Uruchomiona `vsce env create` lub `vsce env select` automatycznie doda `kubectl` kontekstu konfiguracji dla Ciebie, więc kubectl już powinny być podłączone do klastra VSCE Kubernetes. Przykłady:
- Upewnij się, bieżącego kontekstu: `kubectl config current-context`
- Wyświetl listę wszystkich dostępnych kontekstach: `kubectl config get-contexts`. Klastra kubernetes utworzone przez VSCE będzie miała nazwę przypominać "vsce -<guid>".
- Kontekst zmiany: `kubectl config use-context <context-name>`
- Wyświetlić pulpit nawigacyjny Kubernetes: Uruchom `kubectl proxy`, Otwórz w przeglądarce adres, który emituje to polecenie (Dołącz `/ui` do adresu URL, aby przejść do pulpitu nawigacyjnego Kubernetes).
- Listy uruchomionych usług w domyślnej przestrzeni VSCE o nazwie *mainline*: `kubectl get services --namespace=mainline`

