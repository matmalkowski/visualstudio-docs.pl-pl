---
title: "R Tools for Visual Studio — często zadawane pytania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e656ac64-915a-40bb-8196-93d33250ef98
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 79420e09f7ca0b01ce97fc19a063a8b15431b544
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="frequently-asked-questions"></a>Często zadawane pytania

## <a name="visual-studio-support"></a>Obsługa programu Visual Studio

**Q. RTVS działa na OS X lub Linux?**

. RTVS obecnie bazuje na Visual Studio, która jest implementacją tylko do systemu Windows. Firma Microsoft bada obsługi w programie Visual Studio Code i Visual Studio dla komputerów Mac. Zapoznaj się [RTVS wystawiać #1295](https://github.com/Microsoft/RTVS/issues/1295).

**Q. RTVS działa w przypadku wersji programu Visual Studio Express?**

. Nie.

**Q. Z RTVS można użyć rozszerzenia programu Visual Studio?**

. Absolutnie. W rzeczywistości poniżej przedstawiono kilka, które są popularne dla osób, Praca z R.

- [VsVim dla powiązań klucza vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [Github](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Edytor markdown z podglądem na żywo](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Zobacz [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Aby uzyskać więcej informacji.

**Q. Ponieważ RTVS znajduje się w programie Visual Studio, to znaczy R mogą być łatwo używane z C#, C++ i innych języków Microsoft?**

. Nie. RTVS jest narzędziem służącym do tworzenia kodu języka R i używa standardowych natywnego tłumaczy R. Współdziałanie między R i innych języków nie jest obecnie obsługiwany.

**Q. RTVS działa z ustawień regionalnych innych niż angielskie?**

. W wersji 1.0 RTVS jest tylko do języka angielskiego. Wersji 1.1 będzie lokalizowany do tego samego zestawu języki, które program Visual Studio samej siebie. W międzyczasie, użyj [angielski pakiet językowy dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157), lub w Visual Studio 2017 r, należy uruchomić Instalatora i wybrać język angielski w **pakiety językowe** kartę.

![Ustawienia międzynarodowe dla programu Visual Studio 2017 r.](media/FAQ-international-settings.png)

**Q. Podoba naprawdę Moje bieżące ustawienia programu Visual Studio, ale chcę wypróbować nowe ustawienia analizy danych. Co należy zrobić?**

. Zapisz bieżące ustawienia programu Visual Studio przy użyciu **Narzędzia > Import i eksport ustawień...** , następnie przejdź do ustawień analizy danych. Aby przywrócić zapisane ustawienia, należy użyć **Import i eksport ustawień...**  polecenie ponownie.

**Q. Czy mogę przechowywać w udziale sieciowym projektu programu Visual Studio?**

. Nie, Visual Studio nie obsługuje ładowania projektów z udziału sieciowego.

## <a name="r-interpretersintegration"></a>R tłumaczy/integracji

**Q. Jakie tłumaczy R RTVS działa z?**

. [R sieci CRAN](https://cran.r-project.org/), [klienta Microsoft R i Microsoft Machine Learning serwera](/machine-learning-server/)

**Q. Gdzie można pobrać te tłumaczy?**

. Zobacz [instalacji](installation.md).

Q **co to jest Microsoft R Server?**

. Serwer R jest poprzednia nazwa [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**Q. RTVS działa z 32-bitowe wersje R?**

. Nie, RTVS obsługuje tylko 64-bitowe wersje R systemem 64-bitowych wersji systemu Windows.

**Q. RTVS działa z mojej systemu kontroli źródła?**

. Tak, można użyć do systemu kontroli źródła, który jest zintegrowany z programu Visual Studio.

**Q. Co to są zalecane `.gitignore` ustawień dla projektu RTVS?**

. Głównym repozytorium przechowuje Github zalecane `.gitignore` plików. Można to sprawdzić tutaj: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Usługi zdalne

Q. **Co to jest zdalny w programie Visual Studio?**

. Usługi zdalnego R dla programu Visual Studio umożliwia konfigurowanie komputera z systemem Windows lub Linux, a następnie podłącz do niego z RTVS. Zobacz [Konfigurowanie zdalnych obszarów roboczych](workspaces-remote-setup.md).

Q. **Czy RTVS można połączyć się serwerem R firmy Microsoft?**

. Nie, ponieważ R serwera jest różne technologie i nie zapewnia sam mechanizm łączności jako wymagany przez RTVS.

Q. **RTVS można podłączyć do maszyny Wirtualnej utworzonej przy użyciu obrazu maszyny Wirtualnej nauki danych na platformie Azure?**

. Tak; Obraz maszyny Wirtualnej nauki danych preinstalowane dzięki usługom R zdalnego dla programu Visual Studio.

Q, **RTVS można połączyć się z komputerem zdalnym z języka R zainstalowanego?**

Wykonanie kodu języka R na zdalnym komputerze, musi istnieć niektóre usługi nasłuchiwanie żądań, kod odbieranie i wysyłanie wyniki z powrotem do komputera klienckiego. Jest to, czy usługi R zdalnego dla programu Visual Studio. Zobacz [Konfigurowanie zdalnych obszarów roboczych](workspaces-remote-setup.md).

Q. **Co to jest sesji zdalnej?**

. Zapoznaj się z artykułem [wykonaj na serwerze zdalnym](/machine-learning-server/r/how-to-execute-code-remotely) w dokumentacji Machine Learning serwera.

## <a name="rtvs-development-and-features"></a>Programowanie RTVS i funkcje

**Q. Brak funkcji X, ale programu RStudio zostało ono!**

. Programu RStudio jest przyciągają i dojrzałe IDE dla języka R, która została opracowywane przez wiele lat. RTVS stara się o wszystkich funkcji krytycznych, które są potrzebne do pomyślnego. Pomóc ustalić ich priorytety przyszłe zadania, wykonując [ankiety RTVS](https://www.surveymonkey.com/r/RTVS1) i problemy dotyczące plików na [GitHub](https://github.com/Microsoft/RTVS/issues/).

**Q. Można współtworzyć na RTVS?**

. Jak najbardziej! Kod źródłowy znajduje się [Github](https://github.com/microsoft/RTVS). Śledzenie problem umożliwia zgłaszanie błędów i dodać komentarz dotyczący tych już złożony.

Zachęcamy do ich współtworzenia tej dokumentacji&mdash;po prostu wybierz **Edytuj** polecenia w prawym górnym rogu każdej strony. Komentarze dotyczące dokumentów są również powitalny, który można dodać u dołu każdej strony.
