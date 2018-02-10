---
title: "R Tools for Visual Studio — często zadawane pytania | Dokumentacja firmy Microsoft"
description: "Często zadawane pytania na R w programie Visual Studio."
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 5d6ede092549a3f055c15b1f7deafe0421797c44
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="frequently-asked-questions"></a>Często zadawane pytania

## <a name="visual-studio-support"></a>Obsługa programu Visual Studio

**Q. RTVS działa na OS X lub Linux?**

A. RTVS obecnie bazuje na Visual Studio, która jest implementacją tylko do systemu Windows. Firma Microsoft bada obsługi w programie Visual Studio Code i Visual Studio dla komputerów Mac. Zapoznaj się [RTVS wystawiać #1295](https://github.com/Microsoft/RTVS/issues/1295).

**Q. RTVS działa w przypadku wersji programu Visual Studio Express?**

A. Nie.

**Q. Z RTVS można użyć rozszerzenia programu Visual Studio?**

A. Absolutnie. W rzeczywistości poniżej przedstawiono kilka, które są popularne dla osób, Praca z R.

- [VsVim dla powiązań klucza vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [Github](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Edytor markdown z podglądem na żywo](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Zobacz [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Aby uzyskać więcej informacji.

**Q. Ponieważ RTVS znajduje się w programie Visual Studio, to znaczy R mogą być łatwo używane z C#, C++ i innych języków Microsoft?**

A. Nie. RTVS jest narzędziem służącym do tworzenia kodu języka R i używa standardowych natywnego tłumaczy R. Współdziałanie między R i innych języków nie jest obecnie obsługiwany.

**Q. RTVS działa z ustawień regionalnych innych niż angielskie?**

A. W wersji 1.0 RTVS jest tylko do języka angielskiego. Wersji 1.1 będzie lokalizowany do tego samego zestawu języki, które program Visual Studio samej siebie. W międzyczasie, użyj [angielski pakiet językowy dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157), lub w Visual Studio 2017 r, należy uruchomić Instalatora i wybrać język angielski w **pakiety językowe** kartę.

![Ustawienia międzynarodowe dla programu Visual Studio 2017 r.](media/FAQ-international-settings.png)

**Q. Podoba naprawdę Moje bieżące ustawienia programu Visual Studio, ale chcę wypróbować nowe ustawienia analizy danych. Co należy zrobić?**

A. Zapisz bieżące ustawienia programu Visual Studio przy użyciu **Narzędzia > Import i eksport ustawień...** , następnie przejdź do ustawień analizy danych. Aby przywrócić zapisane ustawienia, należy użyć **Import i eksport ustawień...**  polecenie ponownie.

**Q. Czy mogę przechowywać w udziale sieciowym projektu programu Visual Studio?**

A. Nie, Visual Studio nie obsługuje ładowania projektów z udziału sieciowego.

## <a name="r-interpretersintegration"></a>R tłumaczy/integracji

**Q. Jakie tłumaczy R RTVS działa z?**

A. [R sieci CRAN](https://cran.r-project.org/), [klienta Microsoft R i Microsoft Machine Learning serwera](/machine-learning-server/)

**Q. Gdzie można pobrać te tłumaczy?**

A. Zobacz [instalacji](installing-r-tools-for-visual-studio.md).

Q **co to jest Microsoft R Server?**

A. Serwer R jest poprzednia nazwa [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**Q. RTVS działa z 32-bitowe wersje R?**

A. Nie, RTVS obsługuje tylko 64-bitowe wersje R systemem 64-bitowych wersji systemu Windows.

**Q. RTVS działa z mojej systemu kontroli źródła?**

A. Tak, można użyć do systemu kontroli źródła, który jest zintegrowany z programu Visual Studio.

**Q. Co to są zalecane `.gitignore` ustawień dla projektu RTVS?**

A. Głównym repozytorium przechowuje Github zalecane `.gitignore` plików. Można to sprawdzić tutaj: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Usługi zdalne

Q. **Co to jest zdalny w programie Visual Studio?**

A. Usługi zdalnego R dla programu Visual Studio umożliwia konfigurowanie komputera z systemem Windows lub Linux, a następnie podłącz do niego z RTVS. Zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md).

Q. **Czy RTVS można połączyć się serwerem R firmy Microsoft?**

A. Nie, ponieważ R serwera jest różne technologie i nie zapewnia sam mechanizm łączności jako wymagany przez RTVS.

Q. **RTVS można podłączyć do maszyny Wirtualnej utworzonej przy użyciu obrazu maszyny Wirtualnej nauki danych na platformie Azure?**

A. Tak; [danych nauki VM - Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) obrazu preinstalowane dzięki usługom R zdalnego dla programu Visual Studio.

Q, **RTVS można połączyć się z komputerem zdalnym z języka R zainstalowanego?**

Wykonanie kodu języka R na zdalnym komputerze, musi istnieć niektóre usługi nasłuchiwanie żądań, kod odbieranie i wysyłanie wyniki z powrotem do komputera klienckiego. Jest to, czy usługi R zdalnego dla programu Visual Studio. Zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md).

Q. **Co to jest sesji zdalnej?**

A. Zapoznaj się z artykułem [wykonaj na serwerze zdalnym](/machine-learning-server/r/how-to-execute-code-remotely) w dokumentacji Machine Learning serwera.

## <a name="rtvs-development-and-features"></a>Programowanie RTVS i funkcje

**Q. Brak funkcji X, ale programu RStudio zostało ono!**

A. Programu RStudio jest przyciągają i dojrzałe IDE dla języka R, która została opracowywane przez wiele lat. RTVS stara się o wszystkich funkcji krytycznych, które są potrzebne do pomyślnego. Pomóc ustalić ich priorytety przyszłe zadania, wykonując [ankiety RTVS](https://www.surveymonkey.com/r/RTVS1) i problemy dotyczące plików na [GitHub](https://github.com/Microsoft/RTVS/issues/).

**Q. Można współtworzyć na RTVS?**

A. Jak najbardziej! Kod źródłowy znajduje się [Github](https://github.com/microsoft/RTVS). Śledzenie problem umożliwia zgłaszanie błędów i dodać komentarz dotyczący tych już złożony.

Zachęcamy do ich współtworzenia tej dokumentacji&mdash;po prostu wybierz **Edytuj** polecenia w prawym górnym rogu każdej strony. Komentarze dotyczące dokumentów są również powitalny, który można dodać u dołu każdej strony.
