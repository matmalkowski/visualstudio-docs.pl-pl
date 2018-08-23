---
title: Parametry połączenia zawierają poświadczenia z hasła w postaci zwykłego tekstu, a nie korzysta ze zintegrowanych zabezpieczeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d1be15ffdc204512c3034662b6ca24955869f5c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682413"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Parametry połączenia zawierają poświadczenia z hasłem w postaci zwykłego tekstu i nie korzystają ze zintegrowanych zabezpieczeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [parametry połączenia zawierają poświadczenia z hasła w postaci zwykłego tekstu, a nie korzysta ze zintegrowanych zabezpieczeń](https://docs.microsoft.com/visualstudio/data-tools/the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security).  
  
  
Czy chcesz zapisać parametry połączenia w bieżącym pliku DBML i pliki konfiguracyjne aplikacji z tymi informacjami poufnymi?  Kliknij przycisk nie, aby zapisać parametry połączenia bez informacji poufnych.  
  
 Podczas pracy z połączeniami danych, zawierające informacje poufne (hasła, które znajdują się w parametrach połączenia), możesz skorzystać z opcji zapisanie parametrów połączenia w pliku DBML projektu i pliku konfiguracji aplikacji z użyciem lub bez poufne informacje.  
  
> [!WARNING]
>  Jawne ustawianie **połączenia** właściwości **ustawienia aplikacji** właściwości **False** spowoduje dodanie hasła do pliku DBML.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Aby zapisać parametry połączenia z poufnych informacji w ustawieniach aplikacji projektu  
  
-   Kliknij przycisk **Tak**.  
  
     Parametry połączenia są przechowywane jako ustawienie aplikacji. Parametry połączenia zawierają poufne informacje w postaci zwykłego tekstu. Za pomocą pliku DBML nie zawiera poufne informacje.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Aby zapisać parametry połączenia bez informacji poufnych w ustawieniach aplikacji projektu  
  
-   Kliknij przycisk **nie**.  
  
     Parametry połączenia są przechowywane jako ustawienie aplikacji, ale hasło nie jest dołączony.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

