---
title: "Visual Studio Test Professional 2017 obciążenia i składnik identyfikatorów | Dokumentacja firmy Microsoft"
description: "Umożliwia podanie zintegrowane narzędzia do testowania generalist testerów identyfikatorów obciążenia i składników programu Visual Studio"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 10/09/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-ide-install
ms.assetid: 70c03438-8434-4921-ada0-c172519af431
ms.openlocfilehash: 82375aa5b08b3890aa2c615f9d44877ca7fb3a22
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2017
---
# <a name="visual-studio-test-professional-2017-component-directory"></a>Visual Studio Test Professional 2017 składników katalogu

Tabele zawierają na tej stronie listę identyfikatorów, które można zainstalować program Visual Studio przy użyciu wiersza polecenia. Należy pamiętać, że będą dodawane dodatkowe składniki jako wydania aktualizacji dla programu Visual Studio.

Należy również zauważyć następujące kwestie dotyczące tej strony:

* Każde obciążenie ma osobny rozdział następuje identyfikator obciążenia i spisu składników, które są dostępne dla obciążeń.
* Domyślnie **wymagane** składników zostanie zainstalowany po zainstalowaniu obciążenie. Jeśli zostanie wybrana, można także zainstalować **zalecane** i **opcjonalnie** składników.
* Dodaliśmy również sekcja, która zawiera listę dodatkowych składników, które nie są powiązane z dowolnym obciążeniu.

Aby uzyskać więcej informacji na temat używania tych identyfikatorów, zobacz [użyć parametrów wiersza polecenia do zainstalowania programu Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) strony. Oraz listę obciążenia i identyfikatory składników dla innych produktów, zobacz [obciążenia 2017 r w usłudze Visual Studio i identyfikatory składników](workload-and-component-ids.md) strony.

## <a name="test-professional"></a>Test Professional

**Identyfikator:** Microsoft.VisualStudio.Workload.TestProfessional

**Opis:** Test Professional zapewnia zintegrowane narzędzia do testowania dla testerów generalist, które pozwalają dysków ich potrzeb testowania w całym cyklu ich życia testowych.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.0.26711.1 | Wymagane
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.0.26606.0 | Wymagane

## <a name="unaffiliated-components"></a>Odłączony składników

Są to składniki, które nie są dołączone każde obciążenie, ale można wybrać jako poszczególnych składników.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
n/d | n/d | n/d

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) stronę porady dotyczące rozwiązywania problemów. Jak również zgłosić problemy produktu z nami za pośrednictwem [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia w programie Visual Studio IDE lub udział sugestia z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579). Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi. Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio) (wymaga [GitHub](https://github.com/) konta).

## <a name="see-also"></a>Zobacz także

* [Visual Studio obciążenia i składnik identyfikatorów](workload-and-component-ids.md)
* [Przewodnik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykłady parametru wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie w trybie offline instalację programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
