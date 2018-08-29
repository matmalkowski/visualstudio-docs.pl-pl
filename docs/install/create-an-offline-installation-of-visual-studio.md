---
title: Tworzenie instalacji Offline programu Visual Studio
description: Dowiedz się, jak zainstalować program Visual Studio w tryb offline.
ms.custom: ''
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d19eabe10234ca2a1670ae04f99a45a85a6cac14
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138880"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Tworzenie instalacji offline programu Visual Studio 2017

Został zaprojektowany Instalator programu Visual Studio 2017 w taki sposób, aby działać równie dobrze na cały szereg warunków sieciowych i maszyny.

- Nowy model oparty na obciążeniu oznacza, że musisz pobrać daleko mniejsze niż w poprzednich wersjach programu Visual Studio: zaledwie 300 MB do najmniejszej instalacji;
- W porównaniu do ogólnego "ISO" lub plik zip, możemy pobrać pakiety potrzebne dla maszyny. Na przykład firma Microsoft nie pobieraj 64-bitowych plików Jeśli nie trzeba ich;
- W procesie instalacji spróbujemy trzy technologie pobierania różnych (WebClient, BITY i WinInet) aby zminimalizować zakłócenia przy użyciu oprogramowania antywirusowego i serwera proxy;
- Pliki, musisz zainstalować program Visual Studio są dystrybuowane w sieci globalne dostarczanie, dzięki czemu firma Microsoft może udostępnić je użytkownikom z lokalnym serwerem.

Zaleca się, że próbujesz [Instalator sieci web programu Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)&mdash;uważamy, że znajdziesz ją dobre środowisko.

 > [!div class="button"]
 > [Pobierz program Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

Jeśli chcesz zainstalować w trybie offline, ponieważ połączenie z Internetem jest niedostępne lub niestabilne, zobacz [instalacji programu Visual Studio 2017 w powolnych lub zawodnych środowiskach sieciowych](../install/install-vs-inconsistent-quality-network.md). W wierszu polecenia można użyć do utworzenia lokalnej pamięci podręcznej pliki potrzebne do ukończenia instalacji w trybie offline. Ten proces zastępuje pliki ISO dostępne dla wcześniejszych wersji.

> [!NOTE]
> Jeśli jesteś administratorem przedsiębiorstwa, który chce wykonać wdrożenie programu Visual Studio 2017 do sieci z stacje robocze klienta, które są zaporą z Internetu, zobacz nasze [Tworzenie instalacji sieciowej programu Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) i [Instalowanie certyfikatów wymaganych do instalacji w trybie offline programu Visual Studio](../install/install-certificates-for-visual-studio-offline.md) stron.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]
