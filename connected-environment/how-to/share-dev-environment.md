---
title: Jak udostępnić środowiska programistycznego | Dokumentacja firmy Microsoft
author: ghogen
ms.author: ghogen
ms.date: 3/12/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: douge
ms.openlocfilehash: 43d23caa039340345372076d02b3c4989cde5b01
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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