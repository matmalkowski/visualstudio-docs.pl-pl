---
title: "Visual Studio Feedback klienta 2017 obciążenia i składnik identyfikatorów | Dokumentacja firmy Microsoft"
description: "Użyj identyfikatorów obciążenia i składników programu Visual Studio zapewnia bogaty opinii dla Visual Studio Team Services lub Team Foundation Server"
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
ms.technology: vs-acquisition
ms.assetid: 7392a100-100c-458c-9394-828695109015
ms.workload: multiple
ms.openlocfilehash: 27d0f817bb74e833359faaffbc467f2344d166eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-feedback-client-2017-component-directory"></a>Visual Studio Feedback klienta 2017 składników katalogu

Tabele zawierają na tej stronie listę identyfikatorów, które można zainstalować program Visual Studio przy użyciu wiersza polecenia. Należy pamiętać, że będą dodawane dodatkowe składniki jako wydania aktualizacji dla programu Visual Studio.

Należy również zauważyć następujące informacje o stronie:

* Każde obciążenie ma osobny rozdział następuje identyfikator obciążenia i spisu składników, które są dostępne dla obciążeń.
* Domyślnie **wymagane** składników zostanie zainstalowany po zainstalowaniu obciążenie. Jeśli zostanie wybrana, można także zainstalować **zalecane** i **opcjonalnie** składników.
* Dodaliśmy również sekcja, która zawiera listę dodatkowych składników, które nie są powiązane z dowolnym obciążeniu.

Aby uzyskać więcej informacji na temat używania tych identyfikatorów, zobacz [użyć parametrów wiersza polecenia do zainstalowania programu Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) strony. Oraz listę obciążenia i identyfikatory składników dla innych produktów, zobacz [obciążenia 2017 r w usłudze Visual Studio i identyfikatory składników](workload-and-component-ids.md) strony.

## <a name="feedback-client"></a>Feedback Client

**Identyfikator:** Microsoft.VisualStudio.Workload.FeedbackClient

**Opis:** Feedback client umożliwia zainteresowanym w celu otrzymania opinii sformatowanego dla Visual Studio Team Services lub program Team Foundation Server.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.0.27005.2 | Wymagane

## <a name="unaffiliated-components"></a>Odłączony składników

Są to składniki, które nie są dołączone każde obciążenie, ale można wybrać jako poszczególnych składników.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
n/d | n/d | n/d

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:
* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi.
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio).  (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Przewodnik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
