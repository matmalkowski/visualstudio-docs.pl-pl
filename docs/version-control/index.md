---
layout: LandingPage
title: Kontrola wersji programu Visual Studio | VSTS & TFS
description: Przewodnik Wprowadzenie do korzystania z kontroli wersji w Viual Studio
keywords: Kontrola wersji programu VSTS, TFS,
author: steved0x
ms.manager: douge
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: article
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.openlocfilehash: 471e0cf7640f07c946e2808621233c6ae20b35c7
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="version-control-in-visual-studio"></a>Kontrola wersji programu Visual Studio

Systemów kontroli wersji pomocne w śledzeniu zmian kodu w czasie. Po wprowadzeniu dowolnych zmian system kontroli wersji wykonuje migawkę plików. System kontroli wersji trwale zapisuje tej migawki, więc można odwołanie go później, jeśli zajdzie taka potrzeba. Program Visual Studio udostępnia [Git](/vsts/git/index) i [kontroli wersji typu Team Foundation (TFVC)](/vsts/tfvc/index). Aby zdecydować, między tymi dwoma systemami, zobacz [Wybór właściwej wersji formantu w projekcie](/vsts/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json).

## <a name="git"></a>Git
Git to system kontroli wersji najczęściej używanych dzisiaj i szybko staje się standard kontroli wersji. Git to system kontroli wersji rozproszonej, co oznacza, że kopii lokalnej kodu jest repozytorium kontroli pełną wersję. Te pełni funkcjonalne repozytoriów lokalnych przeprowadzić łatwo pracować w trybie offline lub zdalnie. Przekaż lokalnie swoją pracę, a następnie zsynchronizować kopię repozytorium z kopią na serwerze. Ten model różni się od kontroli wersji scentralizowane, gdzie klienci muszą synchronizować kodu z serwerem przed utworzeniem nowej wersji kodu.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="https://www.visualstudio.com/learn-git/">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Dowiedz się Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/vsts/git/share-your-code-in-git-vs-2017?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Rozpoczynanie pracy z usługą Git z programem Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/vsts/git/tutorial/clone?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Klonowanie istniejące repozytorium Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>Kontrola wersji serwera Team Foundation

Team Foundation Version Control (TFVC) to scentralizowany system kontroli wersji. Zazwyczaj członkowie zespołu mają tylko jedną wersję każdego pliku na swoich komputerach deweloperskich. Dane historyczne są utrzymywane tylko na serwerze. Gałęzie bazują na ścieżkach i są tworzone na serwerze.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/vsts/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Dowiedz się TFVC</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/vsts/tfvc/share-your-code-in-tfvc-vs?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Wprowadzenie do programu TFVC w programie Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/vsts/tfvc/get-code-reviewed-vs?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Przegląd kodu</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>


## <a name="resources"></a>Resources 

- [Pro książki Git](https://git-scm.com/book/en/v2)  
- [Zaplanuj migrację Git](https://www.visualstudio.com/learn/centralized-to-git/)  
- [Migracja z programu TFVC do Git](https://www.visualstudio.com/learn/migrate-from-tfvc-to-git/)  

 

