---
title: Jak udostępnić środowiska programistycznego | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 3/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: 9808e1ac3a6d7b3381b807bc0ce209e15f3e97cf
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="share-a-development-environment"></a>Udostępnianie Środowisko deweloperskie

Połączone środowiska umożliwiają udostępnianie środowiska programowania z innymi osobami w zespole. Każdy deweloper może współpracować własnej przestrzeni bez obawy złamanie innych użytkowników. Ponadto pracujących razem w jednym środowisku można włączyć do testowania kodu end-to-end bez konieczności tworzenia mocks lub symulować zależności. Zobacz [więcej informacji na temat tworzenia zespołu](../get-started-nodejs-06.md) przewodnika, aby uzyskać więcej informacji.

Aby skonfigurować środowisko dla wielu deweloperów:
1. [Tworzenie środowisku połączonym na platformie Azure](../get-started.md). Musisz być właścicielem lub współautorem dostępu do wybranej subskrypcji Azure.
1. Konfigurowanie środowiska **grupy zasobów** do [udzielić dostępu współautora](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-configure) dla każdego członka zespołu. Grupy zasobów w środowisku można sprawdzić, uruchamiając poniższe polecenie: `vsce env list`
1. Poproś członkom zespołu **wybierz środowisko** aby tworzyć w nim.
     * **Wiersz polecenia lub kodzie VS**: Aby wyświetlić istniejących środowiskach połączony użytkownik ma dostęp do: `vsce env list`. Wybierz środowisko: `vsce env select`.
     * **Visual Studio IDE**: Otwórz projekt w programie Visual Studio, wybierz **połączone środowisko AKS** z rozwijanej ustawień uruchamiania. W otwartym oknie dialogowym Wybierz istniejące środowisko deweloperskie.

![Visual Studio Uruchom ustawienia listy rozwijanej](../images/LaunchSettings.png)