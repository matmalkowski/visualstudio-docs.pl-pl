---
title: "Instalowanie narzędzi R dla programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.tgt_pltfrm: 
ms.devlang: r
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 2abb64170fdaa7ce91308f1be2c683325bc1abdd
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Instalowanie narzędzi R dla programu Visual Studio

W tym temacie:

- [Obsługiwane wersje programu Visual Studio](#supported-versions-of-visual-studio)
- [Instalowanie RTVS w Visual Studio 2017 r.](#installing-rtvs-in-visual-studio-2017)
- [Instalowanie RTVS w programie Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Instalacja w trybie offline](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Po zainstalowaniu narzędzi R, może zajść potrzeba Konfigurowanie programu Visual Studio dla układu naukowca zoptymalizowane danych, zgodnie z opisem na [opcje](options.md) tematu.

## <a name="supported-versions-of-visual-studio"></a>Obsługiwane wersje programu Visual Studio

R narzędzi dla programu Visual Studio (RTVS) jest obsługiwana w systemie Windows z społeczność (bezpłatnie), Professional i w wersji Enterprise obu [programu Visual Studio 2017](https://www.visualstudio.com/downloads/) i [programu Visual Studio 2015 Update 3 (lub nowszej)](http://go.microsoft.com/fwlink/?LinkId=691129) (bezpośrednie Pobierz).

RTVS nie jest obecnie obsługiwana w programie Visual Studio dla komputerów Mac.

Nie można zainstalować RTVS, jeśli masz tylko program Visual Studio Shell dołączonego z produktami, takie jak Visual Studio Test Professional i SQL Server Management Studio. Visual Studio Shell nie zawiera składniki niezbędne dla RTVS.

## <a name="installing-rtvs-in-visual-studio-2017"></a>Instalowanie RTVS w Visual Studio 2017 r.

1. Uruchom Instalatora programu Visual Studio. (Zobacz [pobiera](https://www.visualstudio.com/downloads/) Jeśli jeszcze nie masz zainstalowanego programu Visual Studio.) W systemie Windows 7, upewnij się, że Instalatorem jest aktualizowana w celu wyświetlenia wersji programu Visual Studio *15,2 kompilacji 26430.12* lub nowszym.

1. Wybierz **nauki dane i aplikacje analitycznych** obciążenia:

    ![Dane nauki i obciążenia aplikacji analityczne w VS2017](media/installation-data-science-workload.png)

1. Ustaw dodatkowe opcje z prawej strony z tą samą nazwą obciążenia. Domyślnie to obciążenie obejmuje F # i obsługi języka Python. Dla języka R, są minimalne wymagania **obsługę języka R**, **Obsługa środowiska uruchomieniowego dla rozwoju R**, i **klienta Microsoft R**.

RTVS jest zainstalowany w: `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio` gdzie `<version>` jest zwykle `2017` i `<edition>` jest `Community`, `Professional`, lub `Enterprise`.

## <a name="installing-rtvs-in-visual-studio-2015"></a>Instalowanie RTVS w programie Visual Studio 2015

Z programem Visual Studio 2015 musisz zainstalować interpreter języka R i narzędzia R oddzielnie.

### <a name="install-an-r-interpreter"></a>Instalowanie interpretera R

RTVS wymaga 64-bitowej instalacji r wersji 3.2.1 lub nowszego z co najmniej jednego z następujących źródeł:

- [Otwórz program Microsoft R](https://mran.microsoft.com/download/)
- [Klient Microsoft R](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [SIECI CRAN R](https://cran.r-project.org/bin/windows/base/)

Otwórz R Microsoft R sieci CRAN zarówno i umożliwiają wielu wersji side-by-side. Klient R firmy Microsoft, jednak obsługuje tylko jedną wersję i zawsze używa najnowszego zainstalowane.

### <a name="install-the-r-tools"></a>Zainstaluj narzędzia R

Pobierz bieżący RTVS dla programu Visual Studio 2015 z [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current). RTVS sprawdza odpowiedniej wersji programu Visual Studio i ułatwia instalowanie interpretera R, jeśli jeszcze.

> [!Note]
> Autonomiczny Instalator RTVS działa tylko w przypadku programu Visual Studio 2015 roku. z programu Visual Studio 2017 r, zainstaluj obsługę R za pośrednictwem [obciążenia nauki dane i aplikacje analitycznych](#installing-rtvs-in-visual-studio-2017) zgodnie z wcześniejszym opisem.

RTVS dla programu Visual Studio 2015 jest instalowany w:`%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Instalacja programu Visual Studio i RTVS w trybie offline

Instalacja w trybie offline jest odpowiednia dla komputerów, które nie są połączone z Internetem:

1. Postępuj zgodnie z instrukcjami, aby utworzyć Instalatora w trybie offline dla używanej wersji programu Visual Studio: 

    - [Visual Studio 2017 r.](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. Dla programu Visual Studio 2015, Pobierz instalatorów RTVS w trybie offline z [https://aka.ms/rtvs-current-zip](https://aka.ms/rtvs-current-zip) i [https://aka.ms/rtvs-remote-zip](https://aka.ms/rtvs-remote-zip). 

1. Instalowanie programu Visual Studio i RTVS z instalatorów w trybie offline.

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do języka R](getting-started-with-r.md)
- [Narzędzia języka R przykładowych projektach](getting-started-samples.md)
- [Uzyskiwanie pomocy](getting-started-help.md)
- [Ustawienia opcji](options.md)
- [Microsoft Machine Learning serwer (dawniej R)](/machine-learning-server/)