---
title: "Przewodnik administratora w usłudze Visual Studio | Dokumentacja firmy Microsoft"
description: "Dowiedz się więcej o sposobie wdrażania programu Visual Studio w środowisku przedsiębiorstwa."
ms.custom: 
ms.date: 05/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c143456d71057071aa953605e2ee60c6aa9c77de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-2017-administrator-guide"></a>Przewodnik administratora w usłudze Visual Studio 2017

W środowiskach przedsiębiorstw jest typowe dla administratorów systemów wdrożyć instalacje dla użytkowników końcowych z udziału sieciowego lub za pomocą oprogramowania do zarządzania systemami. Firma Microsoft zostały zaprojektowane aparat Instalatora programu Visual Studio do obsługi wdrożenia w przedsiębiorstwie, pozwalając administratorom systemów możliwość tworzenia lokalizacji instalacji sieci, aby wstępnie skonfigurować domyślne ustawienia instalacji, aby wdrożyć kluczy produktów podczas procesu instalacji oraz do zarządzania aktualizacjami produktu po pomyślne wdrożenie. Ten Przewodnik administratora zawiera wskazówek na podstawie scenariusza wdrażania w przedsiębiorstwie w środowiskach sieciowych.

## <a name="deploying-visual-studio-2017-in-an-enterprise-environment"></a>Wdrażanie programu Visual Studio 2017 w środowisku przedsiębiorstwa

Visual Studio 2017 można wdrożyć na klienckich stacjach roboczych, tak długo, jak długo każdy komputer docelowy spełnia [minimalnych wymogów instalacji](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). Czy jest wdrażany za pomocą oprogramowania, takiego jak System Center lub plik wsadowy, zazwyczaj należy wykonywać następujące czynności:

1. [Utwórz udział sieciowy, który zawiera pliki produktu Visual Studio](create-a-network-installation-of-visual-studio.md) do lokalizacji sieciowej.

2. [Wybierz obciążeń i składniki](workload-and-component-ids.md) chcesz zainstalować.

3. [Utwórz plik odpowiedzi](automated-installation-with-response-file.md) zawierający domyślne opcje instalacji. Lub też [utworzyć skrypt instalacji](use-command-line-parameters-to-install-visual-studio.md) używającą parametrów wiersza polecenia umożliwiający kontrolowanie instalacji.

4. Opcjonalnie [Zastosuj klucz produktu licencji zbiorczej](automatically-apply-product-keys-when-deploying-visual-studio.md) jako część instalacji skryptu, dzięki czemu użytkownicy nie musieli oddzielnie aktywować oprogramowania.

5. Układ sieci, aby zaktualizować [kontrolowania, kiedy aktualizacje produktu są dostarczane do użytkowników końcowych](controlling-updates-to-visual-studio-deployments.md).

6. Opcjonalnie można ustawić klucze rejestru [kontrolować, jakie są buforowane na klienckich stacjach roboczych](set-defaults-for-enterprise-deployments.md).

7. Użyj technologii wdrażania wyboru można wykonać skryptu generowane w poprzednich krokach na stacjach roboczych deweloperów docelowej.

8. [Odśwież lokalizację sieciową z najnowszymi aktualizacjami](update-a-network-installation-of-visual-studio.md) dla programu Visual Studio za pomocą polecenia używane w kroku 1 regularnie, aby dodać zaktualizowane składniki.

> [!IMPORTANT]
> Należy pamiętać, że instalacje z sieci udziału "zapamiętuje" w lokalizacji źródłowej pochodzą. Oznacza to, Napraw komputer kliencki może być konieczne powrócić do udziału sieciowego, który pierwotnie zainstalowany klient z. Wybierz lokalizację sieciową dokładnie tak, aby powoduje wyrównanie okresu istnienia, który będzie mieć klientów programu Visual Studio 2017 r z systemem w swojej organizacji.

## <a name="visual-studio-tools"></a>Program Visual Studio tools
Mamy kilka narzędzi ułatwiających [wykrywania i Zarządzanie wystąpieniami programu Visual Studio zainstalowanych](tools-for-managing-visual-studio-instances.md) na komputerach klienckich.

> [!TIP]
> Oprócz dokumentacji w podręczniku administratora, jest dobrym źródłem informacji na temat instalacji programu Visual Studio 2017 [blogu Grunwald kondycji](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:
* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi.
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio).  (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także
* [Zainstaluj program Visual Studio 2017 r.](install-visual-studio.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio 2017 r.](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
  * [Obciążenie i identyfikator składnika odwołania](workload-and-component-ids.md)
* [Utworzyć na podstawie sieci instalację programu Visual Studio](create-a-network-installation-of-visual-studio.md)
  * [Zainstaluj certyfikaty wymagane do instalacji w trybie offline program Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Automatyzowanie programu Visual Studio przy użyciu pliku odpowiedzi](automated-installation-with-response-file.md)
* [Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Ustawianie wartości domyślnych dla wdrożeń programu Visual Studio w przedsiębiorstwie](set-defaults-for-enterprise-deployments.md)
* [Wyłączanie lub przenoszenie pamięci podręcznej pakietów](disable-or-move-the-package-cache.md)
* [Aktualizacja Instalacja oparta na sieci programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Sterowanie aktualizacjami na potrzeby wdrożeń programu Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
