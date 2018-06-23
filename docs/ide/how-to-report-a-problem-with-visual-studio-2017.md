---
title: Jak zgłosić problem z programu Visual Studio 2017 r.
description: Dowiedz się, jak zgłosić problem z programu Visual Studio 2017 do firmy Microsoft, aby firma Microsoft może zdiagnozować i rozwiązać ten problem.
ms.custom: ''
ms.date: 03/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f59d12fc6e587287c6aa1b72de3404f6d56f23a
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326144"
---
# <a name="how-to-report-a-problem-with-visual-studio-2017"></a>Jak zgłosić problem z programu Visual Studio 2017 r.

Jeśli wystąpi problem z programem Visual Studio, chcemy wiadomo o nim. Poniżej przedstawiono sposób Zgłoś problem do [społeczność deweloperów](https://developercommunity.visualstudio.com/) tak, aby firma Microsoft może zdiagnozować i rozwiązać ten problem.

## <a name="report-a-problem-by-using-visual-studio"></a>Zgłoś problem za pomocą programu Visual Studio

Aby zgłosić problem dla programu Visual Studio, konieczne jest zainicjowanie raportu z programu Visual Studio lub Instalator programu Visual Studio. Nie można go bezpośrednio za pomocą [społeczność deweloperów](https://developercommunity.visualstudio.com/) witryny sieci Web. Raportowanie za pomocą programu Visual Studio umożliwia informacje diagnostyczne mają zostać automatycznie uwzględnione w raporcie.

![Raport podręczne problem dotyczący społeczność deweloperów usługi Visual Studio](media/report-an-issue.png)

1. W programie Visual Studio, wybierz **pomocy** > **Prześlij opinię** > **zgłosić Problem**.

   > [!TIP]
   > Jeśli nie można ukończyć instalacji programu Visual Studio lub nie masz dostępu do narzędzia opinię w programie Visual Studio, może zgłosić problem przy użyciu **Instalator programu Visual Studio**. Aby to zrobić, wybierz ikonę opinii w prawym górnym rogu **Instalator programu Visual Studio**.

1. Jeśli użytkownik nie jest zarejestrowany, wybierz **logowania**; jest po prawej stronie narzędzia, jak pokazano na poniższym zrzucie ekranu. Postępuj zgodnie z instrukcjami na ekranie do logowania.

   ![Zaloguj się zgłosić problem](../ide/media/sign-in-new-ux.png)

   Po zalogowaniu, możesz zgłosić problem, który występują, lub w przypadku głosu lub komentarz na nim. Można również głosu lub opublikowane komentarz na inny problem, który zostanie wyświetlony.

1. Visual Studio udostępnia interfejs do wyszukania problemu i sprawdź, czy inne osoby mają zgłoszone, zbyt. Jeśli ktoś zgłosił go, "góra głos" go, aby poinformować nas.

   ![Wyszukiwanie i głosów dla podobnych problemów](../ide/media/search-and-vote.png)

1. Jeśli nie możesz znaleźć tego problemu, wybierz **problem nowy raport** w dolnej części ekranu.

   > [!NOTE]
   > **Problem nowy raport** przycisk jest wyświetlany tylko w interfejsie programu Visual Studio dla społeczności deweloperów. Nie można zgłosić problem bezpośrednio na [społeczność deweloperów](https://developercommunity.visualstudio.com/) witryny sieci Web.

1. Utwórz opisowy tytuł problemu, który pomoże nam go rozesłać do poprawne zespołu Visual Studio.

1. Przekaż dodatkowe szczegóły i w miarę możliwości opisz kroki, które spowodowały wystąpienie problemu.

   ![Zgłoś problem nowy](../ide/media/report-new-problem.png)

1. Wybierz **dalej** można przenieść do **załączników** kartę. W tym miejscu można przechwycić bieżącego ekranu do wysłania do firmy Microsoft. Aby dołączyć dodatkowe zrzuty ekranu lub innych plików, wybierz polecenie **Dołącz dodatkowe pliki**.

   ![Dołącz zrzut ekranu do raport o problemie Visual Studio](media/report-a-problem-screenshot.png)

1. Jeśli nie chcesz dołączyć zrzut ekranu lub [rekord reprodukcja](#record-a-repro), wybierz pozycję **dalej** można przenieść do **Podsumowanie** kartę.

1. Wybierz **przesyłania** wysłanie raportu, wraz z żadnych obrazów i plików śledzenia lub zrzut. (Jeśli **przesyłania** przycisk będzie szary, upewnij się, że podano tytuł i opis raportu.)

   Aby dowiedzieć się, jakie dane są zbierane, zobacz [dane zbierane](developer-community-privacy.md#data-we-collect).

## <a name="record-a-repro"></a>Rekord reprodukcja

Pliki zrzutu śledzenia i sterty są przydatne NAS diagnozowania problemów. Cenimy korzystając z **zgłosić Problem** narzędzia, aby rejestrować wszystkie czynności dotyczące reprodukcja i wysyłać dane do firmy Microsoft. Oto jak to zrobić:

1. Po wprowadzeniu tytuł i opis dla tego problemu, wybierz **dalej** można przenieść do **załączników** kartę.

1. Wybierz **rekordu** kartę.

1. W obszarze **Zarejestruj swoje czynności**, wybierz bieżące wystąpienie programu Visual Studio, czy można odtworzyć problem. Jeśli nie możesz na przykład jeśli odpowiada Visual Studio, wybierz  **\<utworzenia nowego wystąpienia >** do rejestrowania akcji w nowym wystąpieniu programu Visual Studio.

1. Wybierz **Rozpocznij rejestrowanie**. Nadaj uprawnienia do uruchamiania narzędzia.

   ![Wybierz polecenie "Rozpocznij nagrywanie" pozwala udostępnić plik zrzutu śledzenia i sterty w raporcie problem Visual Studio](../ide/media/record-dialog-box.png)

1. Gdy **Rejestrator** pojawi się narzędzie, wykonaj kroki, które odtworzenia problemu.

1. Gdy wszystko będzie gotowe, wybierz pozycję **zatrzymać rekordu** przycisku.

1. Poczekaj kilka minut dla programu Visual Studio do gromadzenia i pakiet zarejestrowane informacje.

   Aby dowiedzieć się, jakie dane są zbierane, zobacz [dane zbierane](developer-community-privacy.md#data-we-collect).

## <a name="search-for-solutions-or-provide-feedback"></a>Wyszukaj rozwiązania lub Prześlij opinię

Jeśli nie chcesz lub nie można użyć programu Visual Studio, aby zgłosić problem, istnieje szansa, że problem już został zgłoszony i rozwiązanie zamieszczony na [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) strony.

Jeśli nie masz problem do raportu, ale chcesz wyrazić opinię o produkcie lub sugestię jest miejsce do tego zbyt. Aby uzyskać więcej informacji, zobacz [UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-ide) strony.

## <a name="see-also"></a>Zobacz także

* [Porozmawiaj z nami](../ide/talk-to-us.md)
* [Zgłoś problem z programem Visual Studio dla komputerów Mac](/visualstudio/mac/report-a-problem)
* [Zgłoś problem z C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Społeczność deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/)
* [Prywatność danych społeczność deweloperów](developer-community-privacy.md)