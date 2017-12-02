---
title: "Rozwiązywanie problemów z Azure zdalnego debugowania dla języka Python w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 6dc28135245cae755189174b18000b5c06537b6d
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Zdalne debugowanie narzędzia do rozwiązywania problemów dla języka Python i platformą Azure

Visual Studio nie może dołączyć do [Azure App Service dla zdalnego debugowania](debugging-azure-remote.md) dla żadnego z następujących powodów:

| Przyczyna | Rozwiązanie |
| --- | --- |
| Bez zainstalowanego programu Visual Studio 2013 Update 4 lub nowszy. | Zainstalowanie odpowiedniej wersji z [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| Projekt, który jest wdrożony w usłudze App Service nie jest zgodny otwarty w programie Visual Studio. | Ładowanie właściwy projekt w programie Visual Studio. |
| Projekt nie został wdrożony z konfiguracji debugowania. | Należy ponownie wdrożyć aplikację prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierając **publikowania**. W **ustawienia** , upewnij się, że **debugowania** jest wybranej konfiguracji. |
| Usługa aplikacji nie jest uruchomiona. | Aby uruchomić Eksploratora serwera w programie Visual Studio lub w portalu Azure. |
| Usługi aplikacji nie jest skonfigurowany dla gniazda sieci web. | Przejdź do [portalu Azure](https://portal.azure.com), przejdź do usługi aplikacji, otwórz **Ustawienia > Ustawienia aplikacji** bloku, Włącz **ogólne ustawienia > sieci Web sockets** do **Na**i wybierz **zapisać**. (Należy pamiętać, że **debugowanie** czy opcji wymienionych w tym bloku *nie* dotyczą debugowania języka Python.) |
| `web.debug.config`Zmodyfikowano powodującą wyłączenie serwera proxy debugowania. | Usuń ten plik i ponownie opublikować projekt do usługi App Service, w tym czasie program Visual Studio odtwarza plik. |

Zobacz też:

- [Azure zdalne debugowanie dla języka Python](debugging-azure-remote.md)
