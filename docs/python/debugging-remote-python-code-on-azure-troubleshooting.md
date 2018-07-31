---
title: Rozwiązywanie problemów z debugowaniem zdalnym platformy Azure dla języka Python
description: Jak rozwiązywać problemy podczas próby debugowania aplikacji w języku Python w usłudze Azure App Service przy użyciu programu Visual Studio.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f545fa223aa929b79016352e799d112bceddaf1c
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341466"
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Zdalne narzędzia do rozwiązywania problemów debugowania dla języka Python i platformy Azure

Program Visual Studio nie powiedzie się dołączyć do [usługi Azure App Service dla zdalnego debugowania](debugging-remote-python-code-on-azure.md) dla żadnego z następujących powodów:

| Przyczyna | Rozwiązanie |
| --- | --- |
| Nie masz programu Visual Studio 2013 Update 4 lub nowszy. | Zainstalowanie odpowiedniej wersji z [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). |
| Projekt, który jest wdrażany w usłudze App Service nie jest zgodna co otwartego w programie Visual Studio. | Ładowanie właściwy projekt w programie Visual Studio. |
| Projekt nie został wdrożony za pomocą **debugowania** konfiguracji. | Ponowne wdrażanie aplikacji, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając polecenie **Publikuj**. W **ustawienia** i upewnij się, że **debugowania** jest wybranej konfiguracji. |
| Usługa App Service nie jest uruchomiony. | Uruchom go z **Eksploratora serwera** w programie Visual Studio lub w witrynie Azure portal. |
| Usługa App Service nie jest skonfigurowana dla gniazda sieci web. | Przejdź do [witryny Azure portal](https://portal.azure.com), przejdź do usługi App Service, otwórz **ustawienia** > **ustawienia aplikacji**, Włącz **ustawienia ogólne**  >  **Web sockets** do **na**i wybierz **Zapisz**. (Należy pamiętać, że **debugowanie** opcje widoczne w tym bloku *nie* dotyczą debugowania języka Python.) |
| *Web.Debug.config* została zmodyfikowana, aby wyłączyć serwera proxy debugowania. | Usuń ten plik i ponownie opublikuj projekt w usłudze App Service, w tym czasie program Visual Studio odtwarza plik. |

Zobacz też:

- [Azure dla zdalnego debugowania dla języka Python](debugging-remote-python-code-on-azure.md)
