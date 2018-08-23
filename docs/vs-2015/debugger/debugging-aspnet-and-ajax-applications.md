---
title: Debugowanie aplikacji ASP.NET i AJAX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- debugging ASP.NET Web applications
- debugging [ASP.NET], about ASP.NET debugging
- WCF, debugging
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f81ca66b7f7d4dde596b465211cb92cec5e695ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684104"
---
# <a name="debugging-aspnet-and-ajax-applications"></a>Debugowanie aplikacji ASP.NET i AJAX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [aplikacji debugowanie ASP.NET i AJAX](https://docs.microsoft.com/visualstudio/debugger/debugging-aspnet-and-ajax-applications).  
  
Debugowanie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web jest podobne do debugowania formularza Windows lub innej aplikacji Windows, ponieważ oba rodzaje aplikacji obejmują formantów i zdarzeń. Istnieją jednak również podstawowe różnice między dwoma rodzajami aplikacji:  
  
-   Rejestrowanie informacji o stanie jest bardziej złożone w aplikacji sieci Web.  
  
-   W aplikacji Windows można debugować kodu jest przede wszystkim w jednej lokalizacji. w aplikacji sieci Web kod może być na kliencie i na serwerze. Gdy [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kod to wszystko na serwerze, mogą istnieć JavaScript lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kodu na komputerze klienckim.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przygotowywanie do debugowania ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 W tym artykule opisano kroki, które są wymagane, aby włączyć debugowanie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji.  
  
 [Debugowanie aplikacji sieci Web](../debugger/debugging-web-applications.md)  
 W tym artykule omówiono sposób debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji, w tym aplikacji skryptu z włączoną obsługą technologii AJAX.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)  
 Wyjaśnia, dlaczego tylko mój kod, należy włączyć debugowanie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] wyjątków.  
  
 [Debugowanie i śledzenie Ajax aplikacje — Przegląd](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)  
 W tym artykule omówiono niektóre techniki i narzędzia, które mogą pomóc w debugowaniu kodu AJAX.  
  
 [IntelliTrace](../debugger/intellitrace.md)  
 Debugowanie kodu szybciej przy użyciu funkcji IntelliTrace można rejestrować i przeglądać historię stanu aplikacji bez konieczności ponownego uruchamiania aplikacji, jak często. Można wyświetlić informacje o zdarzenia i wywołania, które występują podczas uruchamiania aplikacji, a następnie rozpocząć debugowanie w tych punktach w czasie. Wymaga programu Visual Studio Ultimate.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie aplikacji sieci Web i skryptu](../debugger/debugging-web-applications-and-script.md)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)



