---
title: Dane prywatne dla raporty problemów
ms.date: 06/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2905cd6fcf9255eb8ba76d636d908651e2254115
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327079"
---
# <a name="developer-community-data-privacy"></a>Prywatność danych społeczność deweloperów

Domyślnie wszystkie informacje w problem raport dotyczący [społeczność deweloperów](https://developercommunity.visualstudio.com/), w tym wszelkie komentarze i odpowiedzi, jest publicznie widoczna. Jest to przydatne, ponieważ umożliwia całej Wspólnoty problemy, rozwiązań i rozwiązania, które zostały znalezione innych użytkowników. Jednak jeśli zajmującym się ochroną prywatności danych lub tożsamości, mieć opcje.

## <a name="identity-privacy"></a>Prywatność tożsamości

Jeśli masz obawy ujawniania swoją tożsamość, [Utwórz nowe konto Microsoft](https://signup.live.com/) nie ujawnia żadnych szczegółowe informacje o Tobie. Aby utworzyć raport, należy użyć tego konta.

## <a name="data-privacy"></a>Prywatność danych

Jeśli masz zajmującym się ochroną prywatności danych, nie umieszczaj wszystkich danych, które chcesz zachować prywatnych w tytule lub zawartość początkowy raport zawsze jest publiczny. Zamiast tego należy utworzyć raport, a następnie zanotuj, będzie wysyłanie szczegółów prywatnie w oddzielnych komentarza. Utworzony raport o problemie możesz określić, kto może zobaczyć odpowiedzi i załączników:

1. Raport został utworzony, wybierz **Dodaj komentarz** do utworzenia prywatnej opis problemu.

1. W edytorze odpowiedzi, za pomocą kontroli poniżej **przesyłania** i **anulować** przyciski, aby określić odbiorców dla odpowiedzi. Wybierz **Viewable moderatorów i oryginalnego plakat** Aby ograniczyć widoczność pracownikom firmy Microsoft i samodzielnie.

   ![Kontrolka prywatności w społeczność deweloperów](media/developer-community-privacy-control.png)

   Tylko osoby, które określisz widoczny komentarz i wszystkie obrazy, łącza lub kodu, który możesz uwzględnić w nim. Wszystkie odpowiedzi w komentarz ma taką samą widoczność jak pierwotnego komentarza. Dotyczy to nawet wtedy, gdy kontrolka prywatności w odpowiedzi nie wyświetla stan ograniczona widoczność poprawnie.

1. Dodaj opis i wszelkie inne informacje, obrazy i załączniki do plików potrzebnych do Twojej reprodukcja. Wybierz **przesyłania** przycisk, aby wysyłać tych informacji przez użytkowników.

   > [!NOTE]
   > Brak limitu 2 GB na załączonych plików i maksymalnie 10 plików. Jeśli chcesz przekazać rozmiar pliku, możesz przesłać nowy raport o problemie lub żądanie adresu URL przesyłania z pracownikiem firmy Microsoft w komentarzu prywatnych.

Ochrona prywatności i przechowywać poufnych informacji poza widok publiczny, należy zachować wszystkie interakcje z firmy Microsoft do odpowiedzi, w obszarze komentarz ograniczona widoczność. Odpowiedzi na inne komentarze może spowodować przypadkowego ujawnienia informacji poufnych.

## <a name="data-we-collect"></a>Dane, które zbieramy

Jeśli **zgłosić problem** jest inicjowana z Instalator programu Visual Studio, zbierane są najnowsze dziennika instalacji.

Jeśli **zgłosić problem** jest inicjowana z programu Visual Studio, zbierane są co najmniej jeden z następujących typów danych:

- Watson i .NET wpisów z dziennika zdarzeń

- Plik dziennika aktywności w pamięci w usłudze Visual Studio

- PerfWatson pliki, jeśli kolekcja Watson jest włączona, z *VSFeedbackPerfWatsonData* folderu

- Pliki dziennika LiveShare, jeśli istnieją, z *VSFeedbackVSRTCLogs* folderu

- Pliki dziennika Xamarin, jeśli istnieją, z *%LOCALAPPDATA%\Xamarin\Logs*

- Pliki dziennika Nuget, jeśli istnieją, z *%TEMP%\NuGetScratch\nuget-dg\nugetSpec.dg*

- Sieci Web debugera plików dziennika, jeśli istnieją:

   - *%Temp%\vscode-Chrome-Debug.txt*

   - *%Temp%\vscode-node-debug2.txt*

   - *%Temp%\vscode-Edge-Debug.txt*

- Zrzut ekranu, jeśli chcesz dołączyć go

- Rejestrowanie danych, jeśli użytkownik chce dołączyć rejestrowania, który zawiera:

   - Kroki do odtworzenia problemu

   - Plik śledzenia ETL

   - Plik zrzutu

   > [!NOTE]
   > Możesz usunąć żadnych danych rejestrowania, który nie chcesz przesłać przed wysłaniem raportu.

## <a name="see-also"></a>Zobacz także

- [Jak zgłosić problem z programem Visual Studio](how-to-report-a-problem-with-visual-studio-2017.md)
- [Prywatność danych raportu problem C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)