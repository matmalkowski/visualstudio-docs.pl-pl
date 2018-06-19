---
title: Jak używać kubectl środowiska połączone z | Dokumentacja firmy Microsoft
author: ghogen
ms.author: ghogen
ms.date: 03/12/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: douge
ms.openlocfilehash: 138dce09e0d53dc47703b9c6f56a7efda4adc255
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31883530"
---
# <a name="use-kubectl-with-a-connected-environment"></a>Użyj `kubectl` o środowisku połączonym

Mają dostęp klastra Kubernetes w środowisku podłączony, i użyj istniejącego Kubernetes narzędzi, takich jak `kubectl`.

Uruchomiona `vsce env create` lub `vsce env select` automatycznie doda `kubectl` kontekstu konfiguracji dla Ciebie, więc kubectl już powinny być podłączone do klastra VSCE Kubernetes. Przykłady:
- Upewnij się, bieżącego kontekstu: `kubectl config current-context`
- Wyświetl listę wszystkich dostępnych kontekstach: `kubectl config get-contexts`. Klastra kubernetes utworzone przez VSCE będzie miała nazwę przypominać "vsce -<guid>".
- Kontekst zmiany: `kubectl config use-context <context-name>`
- Wyświetlić pulpit nawigacyjny Kubernetes: Uruchom `kubectl proxy`, Otwórz w przeglądarce adres, który emituje to polecenie (Dołącz `/ui` do adresu URL, aby przejść do pulpitu nawigacyjnego Kubernetes).
- Listy uruchomionych usług w domyślnej przestrzeni VSCE o nazwie *mainline*: `kubectl get services --namespace=mainline`

