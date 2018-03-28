---
title: Rozwiązywanie problemów z Azure zdalnego debugowania dla języka Python | Dokumentacja firmy Microsoft
description: Jak rozwiązywać problemy podczas próby debugowanie aplikacji Python uruchomionych w usłudze Azure App Service przy użyciu programu Visual Studio.
ms.custom: ''
ms.date: 07/12/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 92429ea893c4eccee75f3a70ffda44eac8f91aa9
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Zdalnego debugowania do rozwiązywania problemów z języka Python i platformą Azure

Visual Studio nie może dołączyć do [Azure App Service dla zdalnego debugowania](debugging-remote-python-code-on-azure.md) dla żadnego z następujących powodów:

| Przyczyna | Rozwiązanie |
| --- | --- |
| Bez zainstalowanego programu Visual Studio 2013 Update 4 lub nowszy. | Zainstalowanie odpowiedniej wersji z [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| Projekt, który jest wdrożony w usłudze App Service nie jest zgodny otwarty w programie Visual Studio. | Ładowanie właściwy projekt w programie Visual Studio. |
| Projekt nie został wdrożony z konfiguracji debugowania. | Należy ponownie wdrożyć aplikację prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierając **publikowania**. W **ustawienia** , upewnij się, że **debugowania** jest wybranej konfiguracji. |
| Usługa aplikacji nie jest uruchomiona. | Aby uruchomić Eksploratora serwera w programie Visual Studio lub w portalu Azure. |
| Usługi aplikacji nie jest skonfigurowany dla gniazda sieci web. | Przejdź do [portalu Azure](https://portal.azure.com), przejdź do usługi aplikacji, otwórz **Ustawienia > Ustawienia aplikacji** bloku, Włącz **ogólne ustawienia > sieci Web sockets** do **Na**i wybierz **zapisać**. (Należy pamiętać, że **debugowanie** czy opcji wymienionych w tym bloku *nie* dotyczą debugowania języka Python.) |
| `web.debug.config` Zmodyfikowano powodującą wyłączenie serwera proxy debugowania. | Usuń ten plik i ponownie opublikować projekt do usługi App Service, w tym czasie program Visual Studio odtwarza plik. |

Zobacz też:

- [Azure zdalnego debugowania dla języka Python](debugging-remote-python-code-on-azure.md)
